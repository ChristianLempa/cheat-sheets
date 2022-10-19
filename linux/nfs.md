# NFS

Network File System (NFS) is a distributed file system protocol originally developed by Sun Microsystems (Sun), available in **[Linux](linux.md)**, allowing a user on a client computer to access files over a computer network much like local storage is accessed. NFS, like many other protocols, builds on the Open Network Computing Remote Procedure Call (ONC RPC) system. NFS is an open IETF standard defined in a Request for Comments (RFC), allowing anyone to implement the protocol.

---

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

