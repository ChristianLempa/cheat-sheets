# iprout2

***iproute2*** is a collection of *userspace* utilities for controlling and monitoring various aspects of [networking](network.md) in the [Linux](../linux/linux.md) kernel, including routing, network interfaces, tunnels, traffic control, and network-related device drivers.

iproute2 is an open-source project released under the terms of version 2 of the GNU General Public License. Its development is closely tied to the development of networking components of the Linux kernel.  As of December, 2013, iproute2 is maintained by Stephen Hemminger and David Ahern. The original author, Alexey Kuznetsov, was responsible for the quality of service (QoS) implementation in the Linux kernel.

iproute2 collection contains the following command-line utilities:

*arpd, bridge, ctstat, dcb, devlink, ip, lnstat, nstat, rdma, routef, routel, rtacct, rtmon, rtstat, ss, tc, and tipc*

Documentation on the filter syntax can be installed via the following command if on a Debian- or Ubuntu-based distribution of Linux:

```bash
sudo apt-get install iproute2-doc
```

## ss

***ss*** - another utility to investigate sockets

### Options

| Option   | Description                            |
|----------|----------------------------------------|
| -4/-6    | list ipv4/ipv6 sockets                 |
| -n       | numeric addresses instead of hostnames |
| -l       | list listening sockets                 |
| -u/-t/-x | list udp/tcp/unix sockets              |
| -p       | Show process(es) that using socket     |

### Show all listening TCP ports, including the corresponding process

```bash
ss -tlp
```

### Show a summary of all ports connecting to 192.168.2.1 via port 80.

```bash
ss -t dst 192.168.2.1:80
```

### Show all SSH-related connections

```bash
ss -t state established '( dport = :ssh or sport = :ssh )'
```

### Display timer information

```bash
ss -tno
```

### Filter connections by TCP state

```bash
ss -t4 state established
```

## See also

- [Official website](https://wiki.linuxfoundation.org/networking/iproute2)
- [Linux Advanced Routing and Traffic Control HOWTO](https://www.tldp.org/HOWTO/Adv-Routing-HOWTO/), A tutorial in exploring and using iproute2
- [IPROUTE2 Utility Suite Documentation](http://www.policyrouting.org/iproute2.doc.html), Complete official documentation
- [iproute2+tc notes](http://www-online.kek.jp/~yasu/ATLAS/QoS/iproute2-notes.html), A collection of documents relating to iproute2 configuration and usage
- [Netstat](netstat.md)
