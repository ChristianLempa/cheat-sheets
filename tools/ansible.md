# Ansible

Ansible is a suite of software tools that enables infrastructure as code. It is open-source and the suite includes software provisioning, configuration management, and application deployment functionality.

Originally written by Michael DeHaan and acquired by Red Hat in 2015, Ansible is designed to configure both Unix-like systems as well as Microsoft Windows. Ansible is agentless, relying on temporary remote connections via [SSH](../linux/ssh.md) or Windows Remote Management which allows [PowerShell](../windows/powershell.md) execution. The Ansible control node runs on most Unix-like systems that are able to run [Python](../linux/python.md), including Windows with WSL installed. System configuration is defined in part by using its own declarative language.

## Table of Contents

1. [Overview](#overview)
1. [Commands](#commands)
1. [Inventory](#inventory)
1. [Playbook](#playbook)
1. [Tasks](#tasks)
1. [Variables](#variables)
1. [Loops](#loops)
1. [Testing](#testing)
1. [Roles](#roles)
1. [Galaxy](#galaxy)
1. [Secrets](#secrets)
    1. [File-level encryption](#file-level-encryption)
    1. [Variable-level encryption](#variable-level-encryption)
1. [Configs](#configs)
1. [Install Ansible on Ubuntu](#install-ansible-on-ubuntu)

## Overview

- Sponsored by Red Hat
- Automates cloud provisioning, configuration management and application deployments
- Agentless, but nodes and the control machine needs Python
- Connect to each node through SSH (WinRM for Windows)
- Idempotent

## Commands

- `ansible` run ad-hoc tasks
- `ansible-inventory` list hosts
- `ansible-playbook` run playbooks

## Inventory

The *inventory* is a file that defines the hosts upon which the tasks in a playbook operate.

- Static inventory

  ```yaml
  hosts:
    vm1:
      ansible_host: 13.79.22.89
    vm2:
      ansible_host: 40.87.135.194
  ```

- Dynamic inventory

  ```yaml
  plugin: azure_rm
  include_vm_resource_groups:
    - learn-ansible-rg
  auth_source: auto
  keyed_groups:
    - prefix: tag
      key: tags
  ```

  Verify that Ansible can discover your inventory

  ```sh
  ansible-inventory --inventory azure_rm.yml --graph

  # @all:
  # |--@tag_dev:
  # |  |--vm_dev_1
  # |  |--vm_dev_2
  # |--@tag_prod:
  # |  |--vm_prod_1
  # |  |--vm_prod_2
  # |--@ungrouped:
  ```

  You can use `ping` module to verify that Ansible can connect to each VM and Python is correctly installed on each node. (*`ping` actually connects over SSH, not ICMP as the name suggests*)

  ```sh
  # ping a specified group
  ansible \
    --inventory azure_rm.yml \
    --user azureuser \
    --private-key ~/.ssh/ansible_rsa \
    --module-name ping \
    tag_Ansible_mslearn
  ```

## Playbook

Here is an example playbook that configures service accounts

```yaml
# playbook.yml
---
- hosts: all
  become: yes                   # apply with `sudo` privilege
  tasks:
    - name: Add service accounts
      user:                     # 'user' module
        name: "{{ item }}"
        comment: service account
        create_home: no
        shell: /usr/sbin/nologin
        state: present
      loop:   # looping
        - testuser1
        - testuser2
```

Run the playbook

```sh
ansible-playbook \
  --inventory azure_rm.yml \
  --user azureuser \
  --private-key ~/.ssh/ansible_rsa \
  playbook.yml
```

Verify by running a command on each host

```sh
ansible \
  --inventory azure_rm.yml \
  --user azureuser \
  --private-key ~/.ssh/ansible_rsa \
  --args "/usr/bin/getent passwd testuser1" \
  tag_Ansible_mslearn
```

Example modules:

```yaml
---
- hosts: demoGroup
  become: true

  tasks:
    - name: Ping
      ping:                  # 'ping' module, no arguments required

    - name: Install nginx
      apt:                   # 'apt' module, install a package
        name: nginx
        state: present

    - name: Find nginx configs
      find:                 # 'find' module, find files
        path: /etc/nginx/conf.d/
        file_type: file

    - name: Ensure Nginx is running
      service:              # 'service' module
        name: nginx
        state: started
```

## Tasks

There are many ways to filter tasks, by tags, by conditions, etc

```yaml
---
  ...
  tasks:
    - name: Install nginx
      apt:                   # 'apt' module, install a package
        name: nginx
        state: present
      tag: nginx

    - name: Find nginx configs
      find:                 # 'find' module, find files
        path: /etc/nginx/conf.d/
        file_type: file
      tag: config

    - name: Ensure Nginx is running
      service:              # 'service' module
        name: nginx
        state: started
      tag: nginx-start
```

```sh
# list available tags in a playbook
ansible-playbook playbook.yml --list-tags

# run tasks tagged 'nginx'
ansible-playbook playbook.yml --tags nginx

# skip tags
ansible-playbook playbook.yml --skip-tags nginx

# start from a task
ansible-playbook playbook.yml --start-at-task 'Find nginx configs'

# run tasks one-by-one
ansible-playbook playbook.yml --step
```

Task conditions using `when`:

```yaml
tasks:
  - name: Upgrade in Redhat
    when: ansible_os_family == "Redhat"
    yum: name=* state=latest

  - name: Upgrade in Debian
    when: ansible_os_family == "Debian"
    apt: upgrade=dist update_cache=yes
```

## Variables

Define variables in inventory files

```ini
[my-hosts]
vm1
vm2
vm3
vm4

[webservers]
vm1
vm2

# variables for 'all'
[all:vars]
temp_file=/tmp/temp1

# variables for 'webserver'
[webservers:vars]
temp_file=/tmp/temp2
```

Use variables in playbooks

```yaml
- hosts: webservers

  tasks:
    - name: Create a file
      file:
        dest: '{{temp_file}}'
        state: '{{file_state}}'
      when: temp_file is defined
```

You can also pass in a variable in command line

```sh
ansible-playbook demo.yml -e file_state=touch
```

## Loops

```yaml
- hosts: localhost
  vars:
    fruits: [apple,orange,banana]

  tasks:
    - name: Show fruits
      debug:
        msg: I have a {{item}}
      with_items: '{{fruits}}'
```

## Testing

Using `--check` flag

```sh
ansible-playbook demo.yml --check
```

## Roles

```sh
# init a role, this creates a bunch of folders and files
ansible-galaxy init testrole1

ls -AF
# .travis.yml  README.md  defaults/  files/  handlers/  meta/  tasks/  templates/  tests/  vars/
```

- `defaults/` for default variable values
- `vars/` override default variable values
- `tasks/` tasks for this role
- `templates/` jinja2 template files for the `template` task

## Galaxy

Install Ansible roles and collections

```sh
# install a role (into ~/.ansible by default)
ansible-galaxy install huxoll.azure-cli

# install a collection
ansible-galaxy collection install azure.azcollection

pip install -r ~/.ansible/collections/ansible_collections/azure/azcollection/requirements-azure.txt
```

## Secrets

### File-level encryption

```sh
# create an encrypted file
ansible-vault enc

# edit an encrypted file
ansible-vault edit demo1.yml

# run an encrypted playbook
ansible-playbook demo1.yml --ask-vault-pass
```

### Variable-level encryption

```sh
ansible-vault encrypt_string --vault-id @prompt mysupersecretstring
```

Use the secret in a playbook

```yaml
- hosts: localhost
  vars:
    secret: !vault |
          $ANSIBLE_VAULT;1.1;AES256
          66613333646138636537363536373431633333353631646164353031303933316533326437366564
          6430613461323339316130626533336165376238316134310a303836356162633363666439353534
          39653865646130346239316137373565623934663238343061663239383139613032636262363565
          6138613861613031650a326230616637396232623630323362386430326464373364323531303631
          32393362326164343566383936633838336166363535383333366237636639636535
  tasks:
  - name: Test variable
    debug:
      var: secret
```

Run the playbook

```sh
ansible-playbook use-secret.yml --ask-vault-pass
```

## Configs

Ansible configs are in `/etc/ansible/ansible.cfg`

```
[defaults]

# control the output format
stdout_callback = yaml
```

## Install Ansible on Ubuntu

### Install PIP

```bash
sudo apt install python3-pip
```

### Install Ansible

```bash
python3 -m pip install ansible
```
