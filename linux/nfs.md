# NFS Cheat-Sheet
## Install NFS
Install NFS Client on Ubuntu
```
sudo apt -y update
sudo apt -y install nfs-common
```

## Client Configuration


## Server Configuration
### Configuration
*TEMP EXAMPLE*:
`/srv/nfs 192.168.1.2(rw,sync,no_root_squash,subtree_check)`

### root rw permissions
Note the **root_squash** mount option. This option is set by default and must be disabled if not wanted.
*Fix:* enable `no_root_squash`in the `/etc/exports` file and reload the permissions with `sudo exportfs -ra`

