# Linux Basics

## Change Hostname

```bash
hostnamectl set-hostname newhostname
```
## Change IP Address in Ubuntu 20.04 LTS
1. Create a new file `/etc/netplan/01-netcfg.yaml`
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    ens3:
      dhcp4: no
      addresses:
        - 192.168.121.221/24
      gateway4: 192.168.121.1
      nameservers:
          addresses: [8.8.8.8, 1.1.1.1]
```
2. Apply changes
```bash
netplay apply
```
## Change IP Address in Ubuntu 22.04 LTS
### gateway4 has been depricated in ubuntu 22.04 release and routes is used instead!
1. Create a new file `/etc/netplan/01-netcfg.yaml`
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    ens3:
      dhcp4: no
      addresses:
        - 192.168.121.221/24
      routes: 
        - to: default
          via: 192.168.121.1
      nameservers:
          addresses: [8.8.8.8, 1.1.1.1]
```
2. Apply changes
```bash
netplay apply
```
