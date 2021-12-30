# CIVO CLI Cheat-Sheet
## Creating Resources
**temporary example**
`civo instance create --hostname=nfs.clcreative.de --sshkey=WSL2@XWIN --initialus  
er=xcad --size=g3.xsmall --diskimage=921fcb64-8abf-4a51-8823-027d9d75c1d4  
The instance nfs.clcreative.de has been created`

PARAMETER | DESCRIPTION
---|---
`--hostname` | 
`--initialuser` |

### Sizes
`civo size ls`

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


### Diskimages
`civo diskimage ls`

ID | NAME
---|---
`9ffb043e-37d8-4b71-80ed-81227564944f` | centos-7
`e1a83a29-d35b-433b-b1cb-4baade48c81a` | debian-10
`67a75d21-3726-4152-8fc9-dcdb51b6e39e` | debian-9 
`880d37ca-372e-4d33-91bd-3122cf56614b` | ubuntu-bionic
`921fcb64-8abf-4a51-8823-027d9d75c1d4` | ubuntu-focal
