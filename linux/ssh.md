---
tags:
    - protocol
    - remote
    - network
    - 22
categories:
    - commands
    - linux
---

# SSH

The Secure Shell Protocol (SSH) is a cryptographic network protocol for operating network services securely over an unsecured network. Its most notable applications are remote login and command-line execution.

SSH applications are based on a client-server architecture, connecting an SSH client instance with an SSH server. SSH operates as a layered protocol suite comprising three principal hierarchical components: the transport layer provides server authentication, confidentiality, and integrity; the user authentication protocol validates the user to the server; and the connection protocol multiplexes the encrypted tunnel into multiple logical communication channels.

SSH was designed on Unix-like operating systems, as a replacement for Telnet and for unsecured remote Unix shell protocols, such as the Berkeley Remote Shell (rsh) and the related rlogin and rexec protocols, which all use insecure, plaintext transmission of authentication tokens.

SSH was first designed in 1995 by Finnish computer scientist Tatu Yl&#246;nen. Subsequent development of the protocol suite proceeded in several developer groups, producing several variants of implementation. The protocol specification distinguishes two major versions, referred to as SSH-1 and SSH-2. The most commonly implemented software stack is OpenSSH, released in 1999 as open-source software by the OpenBSD developers. Implementations are distributed for all types of operating systems in common use, including embedded systems.

This quick reference cheat sheet provides various for using SSH.

## Connecting
Connect to a server (default port 22)
```bash
ssh root@192.168.1.5
```
Connect on a specific port
```bash
ssh root@192.168.1.5 -p 6222
```
Connect via pem file (0400 permissions)
```bash
ssh -i /path/file.pem root@192.168.1.5
```
See: [SSH Permissions](chmod.md#ssh-permissions)

## Executing
Executes remote command
```bash
ssh root@192.168.1.5 'ls -l'
```
Invoke a local script
```bash
ssh root@192.168.1.5 bash < script.sh
```
Compresses and downloads from a server
```bash
ssh root@192.168.1.5 "tar cvzf - ~/source" > output.tgz
```

## SCP

Copies from remote to local
```bash
scp user@server:/dir/file.ext dest/
```
Copies between two servers
```bash
scp user@server:/file user@server:/dir
```
Copies from local to remote 
```bash
scp dest/file.ext user@server:/dir
```
Copies a whole folder
```bash
scp -r user@server:/dir dest/
```
Copies all files from a folder
```bash
scp user@server:/dir/* dest/
```
Copies from a server folder to the current folder
```bash
scp user@server:/dir/* .
```


### Config location
| File Path                | Description          |
|--------------------------|----------------------|
| `/etc/ssh/ssh_config`    | System-wide config   |
| `~/.ssh/config`          | User-specific config |
| `~/.ssh/id_{type}`       | Private key          |
| `~/.ssh/id_{type}.pub`   | Public key           |
| `~/.ssh/known_hosts`     | Logged in host       |
| `~/.ssh/authorized_keys` | Authorized login key |


### SCP Options

| Options       | Description                                    |
|---------------|------------------------------------------------|
| scp `-r`      | <yel>R</yel>ecursively copy entire directories |
| scp `-C`      | <yel>C</yel>ompresses data                     |
| scp `-v`      | Prints <yel>v</yel>erbose info                 |
| scp `-P` 8080 | Uses a specific <yel>P</yel>ort                |
| scp `-B`      | <yel>B</yel>atch mode _(Prevents password)_    |
| scp `-p`      | <yel>P</yel>reserves times and modes           |


### Config sample

```toml
Host server1 
    HostName 192.168.1.5
    User root
    Port 22
    IdentityFile ~/.ssh/server1.key
```

Launch by alias
```bash
ssh server1
```
See: Full [Config Options](https://linux.die.net/man/5/ssh_config)



### ProxyJump

```bash
ssh -J proxy_host1 remote_host2
```

```bash
ssh -J user@proxy_host1 user@remote_host2
```

Multiple jumps
```bash
ssh -J user@proxy_host1:port1,user@proxy_host2:port2 user@remote_host3
```

### ssh-copy-id
```bash
ssh-copy-id user@server
```

Copy to alias server
```bash
ssh-copy-id server1
```

Copy specific key
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```

## SSH keygen

### ssh-keygen

```bash
ssh-keygen -t rsa -b 4096 -C "your@mail.com" 
```

|   | Option | Description                   |
|---|--------|-------------------------------|
|   | `-t`   | [Type](#key-type) of key      |
|   | `-b`   | The number of bits in the key |
|   | `-C`   | Provides a new comment        |

Generate an RSA 4096 bit key with email as a comment


### Generate

Generate a key interactively
```bash
ssh-keygen
```

Specify filename
```bash
ssh-keygen -f ~/.ssh/filename
```

Generate public key from private key
```bash
ssh-keygen -y -f private.key > public.pub
```

Change comment
```bash
ssh-keygen -c -f ~/.ssh/id_rsa
```

Change private key passphrase 
```bash
ssh-keygen -p -f ~/.ssh/id_rsa
```

### Key type

- rsa
- ed25519
- dsa
- ecdsa

### known_hosts

Search from known_hosts
```bash
ssh-keygen -F <ip/hostname>
```

Remove from known_hosts
```bash
ssh-keygen -R <ip/hostname>
```

### Key format

- PEM 
- PKCS8


## See also

- [OpenSSH Config File Examples](https://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/) _(cyberciti.biz)_
- [ssh_config](https://linux.die.net/man/5/ssh_config) _(linux.die.net)_

