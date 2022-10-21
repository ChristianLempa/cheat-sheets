# FTP

## ftp client commands

| Command | Description |
|---------|-------------|
| `binary` | set binary transfer type |
| `cd` | change remote working directory |
| `lcd` | change local working directory |
| `get` | recieve file |
| `mget` | get multiple files |
| `passive` | enter passive transfer mode |
| `ls` | list contents of remote directory |

## Traditional ports, though they can be dynmically assigned

| Port | Description |
|------|-------------|
| Port 21 | control commands |
| Port 20 | data transfer |

## Active mode

Client initiates control session on *port 21* and leaves *port 20* open for the server to send data, and the server initiates the connection for *port 20*.

***If client is behind a firewall, or NAT, then the server might not be able to connect to send data.***

## Passive mode

Server gives the client a port to initiate a connection to for data transfer.

***Most commonly used by browsers, etc.***
