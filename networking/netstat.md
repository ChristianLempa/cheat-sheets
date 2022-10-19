---
tags:
    - network
    - utility
    - port
categories:
    - commands
    - linux
---

# Netstat

In computing, netstat (network statistics) is a command-line network utility that displays network connections for Transmission Control Protocol (both incoming and outgoing), routing tables, and a number of network interface (network interface controller or software-defined network interface) and network protocol statistics. It is available on Unix, Plan 9, Inferno, and Unix-like operating systems including [macOS](../macos/macos.md), [Linux](../linux/linux.md), Solaris and BSD. It is also available on IBM OS/2 and on Microsoft Windows NT-based operating systems including Windows XP, Windows Vista, Windows 7, Windows 8 and Windows 10.

It is used for finding problems in the network and to determine the amount of traffic on the network as a performance measurement. On Linux this program is mostly obsolete, although still included in many distributions.

On Linux, netstat (part of "net-tools") is superseded by ss (part of [iproute2](iproute2.md)). The replacement for netstat -r is ip route, the replacement for netstat -i is ip -s link, and the replacement for netstat -g is ip maddr, all of which are recommended instead.

This quick reference cheat sheet provides various for using netstat command.

## Getting started

### Statistics

All connections on port 80
```bash
netstat -anp | grep :80
```
Netstat Help
```bash
netstat -h
```

### Listening

| Option           | Example              |
|------------------|----------------------|
| `netstat -ltunp` | All Listening ports  |
| `netstat -ltn`   | Listening TCP ports  |
| `netstat -lun`   | Listening UDP ports  |
| `netstat -lx`    | Listening Unix ports |


### Connections

| Option        | Example             |
|---------------|---------------------|
| `netstat -a`  | All connections     |
| `netstat -at` | All TCP connections |
| `netstat -au` | All UDP connections |


### Statistics

| Option        | Example                |
|---------------|------------------------|
| `netstat -s`  | Display statistics     |
| `netstat -st` | Display TCP statistics |
| `netstat -su` | Display UDP statistics |


### Networks

| Option        | Example                               |
|---------------|---------------------------------------|
| `netstat -i`  | Show network interfaces               |
| `netstat -ie` | Show network interfaces extended info |


### Routing

| Option        | Example                                 |
|---------------|-----------------------------------------|
| `netstat -r`  | Show routing table                      |
| `netstat -rn` | Show routing table, don't resolve hosts |


## See also

- [iproute2](iproute2.md)
