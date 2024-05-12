# Vagrant Cheat-Sheet

## General Management

| Command | Description |
| --- | --- |
| `vagrant status` | Outputs status of the vagrant machine |
| `vagrant global-status` | Outputs status of all vagrant machines |
| `vagrant global-status --prune` | Same as above, but prunes invalid entries |

## Managing VMs

| Command | Description |
| --- | --- |
| `vagrant init` | Initialize Vagrant with a Vagrantfile and ./.vagrant directory, using no specified base image.   Before you can do vagrant up, you'll need to specify a base image in the Vagrantfile. |
| `vagrant up` | Starts vagrant environment (also provisions only on the FIRST vagrant up) |
| `vagrant halt` | Stops the vagrant machine |
| `vagrant suspend` | Suspends a virtual machine (remembers state) |
| `vagrant resume` | Resume a suspended machine (vagrant up works just fine for this as well) |
| `vagrant ssh` | Sonnects to machine via SSH |
| `vagrant ssh <box>` | If you give your box a name in your Vagrantfile, you can ssh into it with boxname. Works from any directory. |
| `vagrant destroy` | Stops and deletes all traces of the vagrant machine |
| `vagrant destroy -f` | Same as above, without confirmation |

## Provisioning VMs

| Command | Description |
| --- | --- |
| `vagrant provision` |  Forces reprovisioning of the vagrant machine |
| `vagrant provision --debug` | Use the debug flag to increase the verbosity of the output |
| `vagrant up --provision \| tee provision.log` | Runs `vagrant up`, forces provisioning and logs all output to a file |

## Manage Boxes

| Command | Description |
| --- | --- |
| `vagrant box list` | See a list of all installed boxes on your computer |
| `vagrant box add <box> <url>` | Download a box image to your computer |
| `vagrant box outdated` | Check for updates vagrant box update |
| `vagrant box remove <box>` | Deletes a box from the machine |
| `vagrant package` | Packages a running virtualbox env in a reusable box |
