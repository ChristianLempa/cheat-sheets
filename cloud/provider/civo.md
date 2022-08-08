# Civo

Homepage: [Civo Kubernetes - Fast, Simple, Managed Kubernetes Service - Civo.com](https://www.civo.com/)
Documentation: [Documentation - Civo.com](https://www.civo.com/docs)
Terraform Registry: [Terraform Registry](https://registry.terraform.io/providers/civo/civo/latest)

---

## Civo CLI
Civo CLI is a tool to manage your Civo account from the terminal. Civo CLI is built with Go and distributed as binary files, available for multiple operating systems and downloadable from https://github.com/civo/cli/releases.

### Authentication
In order to use the command-line tool, you will need to authenticate yourself to the Civo API using a special key. You can find an automatically-generated API key or regenerate a new key at [https://www.civo.com/api](https://www.civo.com/api).

### Create Instances
You can create an instance by running `civo instance create` with a hostname parameter, as well as any options you provide.

**Example:**
```
civo instance create --hostname=<your-hostname> --sshkey=<your-ssh-key-name> --initialuser=xcad --size=g3.xsmall --diskimage=921fcb64-8abf-4a51-8823-027d9d75c1d4  
```

**Parameters:**
PARAMETER | LONG VERSION | DESCRIPTION
---|---|---
`-t` | `--diskimage` | the instance's disk image (from 'civo diskimage ls' command)
`-l` | `--firewall` | the instance's firewall you can use the Name or the ID
`-l` | `--firewall` | the instance's firewall you can use the Name or the ID
`-s` | `--hostname` | the instance's hostname
`-u` | `--initialuser` | the instance's initial user
`-r` | `--network` | the instance's network you can use the Name or the ID
`-p` | `--publicip` | This should be either "none" or "create" (default "create")
`-i` | `--size` | the instance's size (from 'civo instance size' command)
`-k` | `--sshkey` | the instance's ssh key you can use the Name or the ID
`-g` | `--tags` | the instance's tags
`-w` | `--wait` | wait until the instance's is ready

**Instance Sizes:**
ID|SIZE|TYPE|CPU|MEMORY|SSD
---|---|---|---|---|---
g3.xsmall|ExtraSmall|Instance|1|1024|25
g3.small|Small|Instance|1|2048|25
g3.medium|Medium|Instance|2|4096|50
g3.large|Large|Instance|4|8192|100
g3.xlarge|ExtraLarge|Instance|6|16384|150
g3.2xlarge|2XLarge|Instance|8|32768|200
g3.k3s.xsmall|ExtraSmall|Kubernetes|1|1024|15
g3.k3s.small|Small|Kubernetes|1|2048|15
g3.k3s.medium|Medium|Kubernetes|2|4096|15
g3.k3s.large|Large|Kubernetes|4|8192|15
g3.k3s.xlarge|ExtraLarge|Kubernetes|6|16384|15
g3.k3s.2xlarge|2XLarge|Kubernetes|8|32768|15

**Diskimages:**
ID | NAME
---|---
`9ffb043e-37d8-4b71-80ed-81227564944f` | centos-7
`e1a83a29-d35b-433b-b1cb-4baade48c81a` | debian-10
`67a75d21-3726-4152-8fc9-dcdb51b6e39e` | debian-9 
`880d37ca-372e-4d33-91bd-3122cf56614b` | ubuntu-bionic
`921fcb64-8abf-4a51-8823-027d9d75c1d4` | ubuntu-focal
