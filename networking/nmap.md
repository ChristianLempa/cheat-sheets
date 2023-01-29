---
tags:
    - linux
    - network
    - networking
    - security
    - scan
    - scanner
categories:
    - linux
    - security
    - tools
---

# NMap

Nmap (Network Mapper) is a network scanner created by Gordon Lyon (also known by his pseudonym Fyodor Vaskovich). Nmap is used to discover hosts and services on a computer network by sending packets and analyzing the responses.

Nmap provides a number of features for probing computer networks, including host discovery and service and operating system detection. These features are extensible by scripts that provide more advanced service detection, vulnerability detection, and other features. Nmap can adapt to network conditions including latency and congestion during a scan.

Nmap started as a [Linux](../linux/linux.md) utility and was ported to other systems including Windows, [macOS](../macos/macos.md), and BSD. It is most popular on Linux, followed by Windows.

## Single target scan:
```shell
nmap [target]
```

## Scan from a list of targets:
```shell
nmap -iL [list.txt]
```

## Scan port for all available A records
Useful when multiple A records are returned by the DNS server
```shell
nmap --script resolveall \
    --script-args newtargets,resolveall.hosts=[target] -p [port]
```

## iPv6:
```shell
nmap -6 [target]
```

## OS detection:
```shell
nmap -O --osscan_guess [target]
```

## Save output to text file:
```shell
nmap -oN [output.txt] [target]
```

## Save output to xml file:
```shell
nmap -oX [output.xml] [target]
```

## Scan a specific port:
```shell
nmap -p [port] [target]
```

## Do an aggressive scan:
```shell
nmap -A [target]
```

## Speedup your scan

-n => disable ReverseDNS

--min-rate=X => min X packets / sec

```shell
nmap -T5 --min-parallelism=50 -n --min-rate=300 [target]
```

## Traceroute:
```shell
nmap -traceroute [target]
```

## Ping scan only: -sP

Don't ping:     -PN <- Useful if a host doesn't reply to a ping.

TCP SYN ping:   -PS

TCP ACK ping:   -PA

UDP ping:       -PU

ARP ping:       -PR

## Example: Ping scan all machines on a class C network
```shell
nmap -sP 192.168.0.0/24
```

## Force TCP scan: -sT
## Force UDP scan: -sU

## Use some script
```shell
nmap --script default,safe
```

Loads the script in the default category, the banner script, and all .nse files in the directory /home/user/customscripts.

```shell
nmap --script default,banner,/home/user/customscripts
```

Loads all scripts whose name starts with http-, such as http-auth and http-open-proxy.

```shell
nmap --script 'http-*'
```

Loads every script except for those in the intrusive category.

```shell
nmap --script "not intrusive"
```

Loads those scripts that are in both the default and safe categories.

```shell
nmap --script "default and safe"
```

Loads scripts in the default, safe, or intrusive categories, except for those whose names start with http-.

```shell
nmap --script "(default or safe or intrusive) and not http-*"
```

## Scan for the heartbleed

-pT:443 => Scan only port 443 with TCP (T:)

```shell
nmap -T5 --min-parallelism=50 -n --script "ssl-heartbleed" -pT:443 127.0.0.1
```

## Show all information (debug mode)

```shell
nmap -d ...
```

## Discover DHCP information on an interface

```shell
nmap --script broadcast-dhcp-discover -e eth0
```

## See also

- [iproute2](iproute2.md)
- [netstat](netstat.md)
- [network](network.md)
- [tls](tls.md)
- [vpn](vpn.md)
