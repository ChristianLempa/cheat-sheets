# Samba

Samba is a free software re-implementation of the SMB networking protocol, and was originally developed by Andrew Tridgell. Samba provides file and print services for various Microsoft Windows clients and can integrate with a Microsoft Windows Server domain, either as a Domain Controller (DC) or as a domain member. As of version 4, it supports Active Directory and Microsoft Windows NT domains.

Samba runs on most Unix-like systems, such as [Linux](../linux/linux.md), Solaris, AIX and the BSD variants, including Apple's [macOS](../macos/macos.md) Server, and macOS client (Mac OS X 10.2 and greater). Samba also runs on a number of other operating systems such as OpenVMS and IBM i. Samba is standard on nearly all distributions of Linux and is commonly included as a basic system service on other Unix-based operating systems as well. Samba is released under the terms of the GNU General Public License. The name Samba comes from SMB (Server Message Block), the name of the proprietary protocol used by the Microsoft Windows network file system.

## External Resources

- https://confluence.jaytaala.com/display/TKB/Create+samba+share+writeable+by+all%2C+group%2C+or+only+a+user

## Setup Shares

Create user:

```
useradd --system me
chown -R me /disk/share
```

Create a Group:

```
sudo groupadd mygroup
```

Add user to the group:

```
sudo useradd me -G mygroup
```

Set permissions to the directory:

```
chgrp -R mygroup /disk/share
chmod g+s /disk/share
```

Allow all users to read and write to your share:

```
[share]
  path = /disk/share
  writeable = yes
  browseable = yes
  public = yes
  create mask = 0644
  directory mask = 0755
  force user = me
```

Allow all linux users which is part of a group to read and write to your share:

```
[share]
  path = /disk/share
  valid users = @mygroup
  writeable = yes
  browseable = yes
  create mask = 0644
  directory mask = 0755
  force user = me
```

Only allowing one user to access our share, we need to assign a samba password:

```
sudo smbpasswd -a me
```

Then we can specify our config that only our `me` user can access our share with read/write permissions:

```
[share]
  path = /disk/share
  valid users = me
  writeable = yes
  browseable = yes
  create mask = 0644
  directory mask = 0755
  force user = me
```

## Other examples

```
# read to some, write to some
[share]
  comment = Ubuntu Share
  path = /your/samba/share
  browsable = yes
  guest ok = yes
  read only = no
  read list = guest nobody
  write list = user1 user2 user3
  create mask = 0755

# read to all, write to some
[share]
  comment = Ubuntu Share
  path = /your/samba/share
  browsable = yes
  guest ok = yes
  read only = yes
  write list = user1 user2 user3
  create mask = 0755
```
