# tcpdump

## Basic Usage

### Capture packets on a particular interface (eth0)

Note that tcpdump (without the '-i eth0') is also valid if you are only using one interface

```shell
tcpdump -i eth0
```

### Capture packets with more detailed output

```shell
tcpdump -i eth0 -nnvvS
```

### Display captured packets in both HEX and ASCII format

```shell
tcpdump -XX -i eth0
```

### Write captured packets into a file (can be read by tools such as Wireshark, Snort, etc)

```shell
tcpdump -w yourfilename.pcap -i eth0
```

### Read packets from a saved packet capture file

```shell
tcpdump -tttt -r yoursavedfile.pcap
```

### Display IP addresses instead of hostnames when capturing packets

```shell
tcpdump -n -i eth0
```

### Capture packets from a particular source/destination IP address

```shell
tcpdump src 192.168.1.1
tcpdump dst 192.168.1.1
```

### Capture packets from a particular source/destination port number

```shell
tcpdump src port 53
tcpdump dst port 21
```

### Capture an entire network's traffic using CIDR notation

```shell
tcpdump net 192.168.1.0/24
```

### Capture traffic to or from a port

```shell
tcpdump port 3389
```

### Display captured packets above or below a certain size (in bytes)

```shell
tcpdump less 64
tcpdump greater 256
```

## Advanced Usage

More complex statements can be formed with the use of logical operators: and(&&), or(||), not(!)

### Examples

### Capture all traffic from 192.168.1.10 with destination port 80 (with verbose output)

```shell
tcpdump -nnvvS and src 192.168.1.10 and dst port 80
```

### Capture traffic originating from the 172.16.0.0/16 network with destination network 192.168.1.0/24 or 10.0.0.0/8

```shell
tcpdump src net 172.16.0.0/16 and dst net 192.168.1.0/24 or 10.0.0.0/8
```

### Capture all traffic originating from host H1 that isn't going to port 53

```shell
tcpdump src H1 and not dst port 22
```

With some complex queries you may have to use single quotes to ignore special characters, namely parentheses 

### Capture traffic from 192.168.1.1 that is destined for ports 80 and 21

```shell
tcpdump 'src 192.168.1.1 and (dst port 80 or 21)'
```
