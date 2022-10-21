# NPING

## Perform a TCP connect() (handshake) with a host

```shell
nping --tcp-connect [target host]
```

## Perform a TCP connect() 

```shell
nping --tcp-connect [target host] [target host] [target host] 
```

## Attempt a TCP handshake on a port range (1-80)

```shell
nping --tcp-connect [target host] -p1-80 -c 1
```

## Send a UDP packet with 50 bytes of random data (to port 53 in this example)

```shell
nping --udp [target host] -p 53 --data-length 100
```

## Send 500 TCP packets at a rate of 50 packets per second

```shell
nping --tcp [target host] --rate 50 -c 500
```

## Send an ARP request to a particular host

```shell
ping --arp [target host] 

## Send ARP requests to all hosts in the 192.168.1.0/24 network

```shell
nping --arp 192.168.1.0/24 
```

## Send an ICMP echo request

```shell
nping [target host] --icmp --icmp-type echo 
```

## Send an ICMP echo reply

```shell
nping google.com --icmp --icmp-type echo-reply
```

## Send a packet with a bad checksum from port 1221 to port 80

```shell
nping --udp --badsum --source-port 1221 -p 80 [target host]
```

## Toggle how verbose the output should be

simply append '-v ' followed by an integer between -4 (no output) and 4 (very verbose)
