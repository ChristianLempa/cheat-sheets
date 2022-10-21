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
1. [Modules](#modules)
1. [Ad Hoc Commands](#ad-hoc-commands)
1. [Playbooks](#playbooks)
1. [Refactoring Playbooks](#refactoring-playbooks)
1. [Target Specific Nodes](#target-specific-nodes)
1. [Metadata with Tags ](#metadata-with-tags)
1. [Files](#files)
1. [Install Ansible on Ubuntu](#install-ansible-on-ubuntu)
## Install Ansible on Ubuntu
## Resources

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

[Example ansible.cfg](ansible.cfg)

```
[defaults]

# control the output format
stdout_callback = yaml
```

## Modules

Ping:

```
ansible all -m ping
```

Gather Facts:

```
ansible all -m gather_facts
```

Gather Facts for only one host:

```
ansible all -m gather_facts --limit 10.0.0.2
```

List Hosts:

```
ansible all --list-hosts
```

## Ad Hoc Commands

Update index repositories with apt

```
ansible all -m apt -a update_cache=true --become --ask-become-pass
```

Install packages with apt:

```
ansible all -m apt -a name=vim --become --ask-become-pass
```

Install the latest package with apt:

```
ansible all -m apt -a "name=vim state=latest" --become --ask-become-pass
```

Upgrade dist with apt:

```
ansible all -m apt -a upgrade=dist --become --ask-become-pass
```

## Playbooks

- `install_nginx.yml`

```yaml
---
- hosts: all
  become: true
  tasks:
    - name: install nginx
      apt:
        name: nginx
        state: latest
        update_cache: yes
      when: ansible_distribution in ["Debian", "Ubuntu"]
      
    - name: install nginx
      dnf:
        name: nginx
        state: latest
        update_cache: yes
      when: ansible_distribution == "CentOS"
```

Execute playbook:

```
ansible-playbook --ask-become-pass install_nginx.yml
```

## Refactoring Playbooks

Our `inventory`:

```
10.0.0.2 apache_package=apache2 php_package=libapache2-mod-php
10.0.0.3 apache_package=httpd php_package=php
```

Our `playbook.yml`:

```yaml
---
- hosts: all
  become: true
  tasks:
    - name: install apache
      package:
        name: 
          - "{{ apache_package }}"
          - "{{ php_package }}"
        state: latest
        update_cache: yes
```

## Target Specific Nodes

Our `inventory`:

```
[web_servers]
10.0.0.2
10.0.0.3

[db_servers]
10.0.0.4

[file_servers]
10.0.0.5
```

Our `playbook.yml`

```yaml
---
# pretasks mandates to run before any other tasks are running
# but ansible runs playbooks from top to bottom
- hosts: all
  become: true
  pre_tasks:
    - name: Install updates for CentOS 
      dnf:
        update_only: yes
        update_cache: yes
      when: ansible_distribution == "CentOS"
      
    - name: Install updates for Debian/Ubuntu 
      apt:
        upgrade: dist
        update_cache: yes
      when: ansible_distribution in ["Debian", "Ubuntu"]
      
# package is used when the name of the package is the same 
# across operating systems
- hosts: web_servers
  become: true
  tasks:
    - name: Install Nginx
      package:
        name:
          - nginx
          - apache2-utils
        state: latest
      
- hosts: db_servers
  become: true
  tasks:
    - name: Install MariaDB for CentOS 
      dnf:
        name: mariadb-server
        state: latest
      when: ansible_distribution == "CentOS"
      
    - name: Install MariaDB for Debian/Ubuntu 
      apt:
        name: mariadb
        state: latest
      when: ansible_distribution in ["Debian", "Ubuntu"]
      
- hosts: file_servers
  become: true
  tasks:
    - name: Install Samba 
      package:
        name: samba
        state: latest
````

Then run it with:

```bash
ansible-playbook --ask-become-pass playbook.yml
```

## Metadata with Tags 

Use tags to only target specific targets.

```yaml
---
- hosts: all
  become: true
  pre_tasks:
  
    - name: Install updates for CentOS 
      tags: always
      dnf:
        update_only: yes
        update_cache: yes
      when: ansible_distribution == "CentOS"
      
    - name: Install updates for Debian/Ubuntu
      tags: always
      apt:
        upgrade: dist
        update_cache: yes
      when: ansible_distribution in ["Debian", "Ubuntu"]

- hosts: web_servers
  become: true
  tasks:
  
    - name: Install Nginx and utilities for CentOS 
      tags: nginx,centos
      dnf:
        name:
          - nginx
          - httpd-tools
      when: ansible_distribution == "CentOS"  
  
    - name: Install Nginx and utilities for Ubuntu
      tags: nginx,ubuntu
      apt:
        name:
          - nginx
          - apache2-utils
        state: latest
      when: ansible_distribution in ["Debian", "Ubuntu"]
      
- hosts: db_servers
  become: true
  tasks:
  
    - name: Install MariaDB for CentOS 
      tags: centos,db,mariadb
      dnf:
        name: mariadb-server
        state: latest
      when: ansible_distribution == "CentOS"
      
    - name: Install MariaDB for Debian/Ubuntu
      tags: ubuntu,db,mariadb
      apt:
        name: mariadb
        state: latest
      when: ansible_distribution in ["Debian", "Ubuntu"]
      
- hosts: file_servers
  become: true
  tasks:
  
    - name: Install Samba 
      tags: samba
      package:
        name: samba
        state: latest
```

To run the playbook against all targets specified in the playbooks:

```bash
ansible-playbook --ask-become-pass playbook.yml
```

To list all the tags in the playbook:

```bash
ansible-playbook --list-tags playbook.yml

playbook: playbook.yml

  play #1 (all): all  TAGS: []
      TASK TAGS: [always]
  
  play #2 (web_servers): all  TAGS: []
      TASK TAGS: [nginx, ubuntu, centos]
      
  play #3 (db_servers): all  TAGS: []
      TASK TAGS: [centos, db, mariadb, ubuntu]
      
  play #4 (file_servers): all  TAGS: []
      TASK TAGS: [samba]
      
```

To only target the tasks with the ubuntu tag, (note: the updates task will still run due to the `always` tag):

```bash
ansible-playbook --tags ubuntu --ask-become-pass playbook.yml
```

For targeting multiple tags:

```bash
ansible-playbook --tags "db,ubuntu" --ask-become-pass playbook.yml
```

## Files

Ansible playbook that uses files to copy to the targets.

Our `files/default.html`:

```html
<html>
  <body>ok</body>
</html>
```

Our `playbook.yml`:

```yaml
---
- hosts: all
  become: true
  pre_tasks:
  
    - name: Install updates for CentOS 
      tags: always
      dnf:
        update_only: yes
        update_cache: yes
      when: ansible_distribution == "CentOS"
      
    - name: Install updates for Debian/Ubuntu
      tags: always
      apt:
        upgrade: dist
        update_cache: yes
      when: ansible_distribution in ["Debian", "Ubuntu"]

- hosts: web_servers
  become: true
  tasks:
  
    - name: Install Nginx and utilities for CentOS 
      tags: nginx,centos
      dnf:
        name:
          - nginx
          - httpd-tools
      when: ansible_distribution == "CentOS"  
  
    - name: Install Nginx and utilities for Ubuntu
      tags: nginx,ubuntu
      apt:
        name:
          - nginx
          - apache2-utils
        state: latest
      when: ansible_distribution in ["Debian", "Ubuntu"]
      
    - name: Copy default html file for website
      tags: nginx
      copy:
        src: default.html
        dest: /var/www/html/index.html
        owner: root
        group: root
        mode: 0644
```

Execute the playbook to deploy the website file:

```bash
ansible-playbook --ask-become-pass playbook.yml
```

We can use another example to unzip a package:

```
---
- hosts: all
  become: true
  pre_tasks:
  
    - name: Install updates for CentOS 
      tags: always
      dnf:
        update_only: yes
        update_cache: yes
      when: ansible_distribution == "CentOS"
      
    - name: Install updates for Debian/Ubuntu
      tags: always
      apt:
        upgrade: dist
        update_cache: yes
      when: ansible_distribution in ["Debian", "Ubuntu"]

- hosts: workstations
  become: true
  tasks:
  
  - name: Ensure unzip is installed
    package:
      name: unzip
      
  - name: Ensure terraform is installed
    unarchive:
      src: https://releases.hashicorp.com/terraform/1.1.7/terraform_1.1.7_linux_amd64.zip
      dest: /usr/local/bin
      remote_src: yes
      mode: 0755
      owner: root
      group: root
```

And then add the workstations group:

```
[web_servers]
10.0.0.2
10.0.0.3

[db_servers]
10.0.0.4

[file_servers]
10.0.0.5

[workstations]
localhost
```

Then run the playbook:

```bash
ansible-playbook --ask-become-pass playbook.yml
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

## Resources

- [Automating App Build and Deployment from a Github Repository](https://medium.com/@rossbulat/ansible-automating-app-build-and-deployment-from-a-github-repository-7d613985f686)
- [Ansible Youtube Series @LearnLinuxTV](https://www.youtube.com/watch?v=3RiVKs8GHYQ&list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70&index=1)
