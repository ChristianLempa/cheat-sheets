# Netplan

Netplan is a utility for configuring network interfaces in modern versions of [Ubuntu](distros/ubuntu.md) and other Linux distributions. Netplan generates the corresponding configuration files for the underlying network configuration subsystem, such as systemd-networkd or NetworkManager.

---
## How to use

Netplan uses YAML configuration files in the `/etc/netplan/` to describe network interfaces, IP addresses, routes, and other network-related parameters.

**Example: `/etc/netplan/01-netcfg.yaml`**
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: true
```

This configuration sets up a DHCP client for the `﻿enp0s3` Ethernet interface, using the ﻿systemd-networkd renderer. 

To apply this configuration, run the following command. 

```sh
sudo netplan apply.
```

You can also test a new Netplan configuration without applying it permanently. This is useful if you want to try out a new network configuration without disrupting your current network connection.

```sh
sudo netplan try
```

---
## Static IP addresses

To define a static IP address in Netplan, you can use the ﻿addresses key in the configuration file for the relevant network interface. Here’s an example configuration file that sets a static IP address of ﻿192.168.1.10 with a net mask of ﻿24 bits for the `﻿enp0s3` Ethernet interface:

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      addresses:
        - 192.168.1.10/24
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
```

In this configuration, the ﻿addresses key sets the static IP address and net mask for the `﻿enp0s3` interface. The ﻿gateway4 key sets the default gateway, and the ﻿nameserver's key sets the DNS servers.

---
## VLANs

**Example 1: Simple VLAN configuration**
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: true
  vlans:
    vlan10:
      id: 10
      link: enp0s3
      dhcp4: true
```

In this configuration, the `﻿enp0s3` Ethernet interface is configured to use DHCP to obtain an IP address. A VLAN with ID 10 is also configured on the `﻿enp0s3` interface, and DHCP is enabled for this VLAN as well. The ﻿link key specifies that the VLAN is associated with the `﻿enp0s3` interface.

**Example 2: Advanced VLAN configuration**
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: true
  vlans:
    vlan10:
      id: 10
      link: enp0s3
      addresses:
        - 192.168.10.2/24
      routes:
        - to: 0.0.0.0/0
          via: 192.168.10.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
```

In this configuration, a VLAN with ID 10 is configured on the `﻿enp0s3` interface, and a static IP address of ﻿`192.168.10.2` with a net mask of ﻿`24` bits is assigned to the VLAN interface. The ﻿routes key specifies a default route via the gateway at `﻿192.168.10.1`. The ﻿nameserver's key sets the DNS servers to `﻿8.8.8.8` and `﻿8.8.4.4`.

## Bridges and Bonding

Bridging and bonding are two techniques used to combine multiple network interfaces into a single logical interface.

### Bonding

Bonding involves combining two or more physical interfaces into a single logical interface, called a bond interface. The bond interface acts like a single network interface, providing higher bandwidth and redundancy. Bonding is often used in high-performance computing environments, where multiple network interfaces are required to handle the high volume of network traffic.

Example 1: Bonding configuration
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: true
    enp0s4:
      dhcp4: true
  bonds:
    bond0:
      interfaces:
        - enp0s3
        - enp0s4
      dhcp4: true
      parameters:
        mode: active-backup
```

In this configuration, two Ethernet interfaces (﻿enp0s3 and ﻿enp0s4) are configured with DHCP to obtain IP addresses. A bond interface (﻿bond0) is also configured, which combines the two Ethernet interfaces into a single logical interface. The ﻿interfaces key specifies the physical interfaces to include in the bond, and the ﻿mode key specifies the bonding mode (in this case, ﻿active-backup).

### Bridging

Bridging involves creating a bridge interface that connects two or more physical interfaces. The bridge interface acts like a virtual switch, allowing devices connected to any of the physical interfaces to communicate with each other as if they were on the same network segment. Bridging is often used to connect two separate network segments or to provide redundancy in case one physical interface fails.

Example 2: Bridging configuration
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: true
    enp0s4:
      dhcp4: true
  bridges:
    br0:
      interfaces:
        - enp0s3
        - enp0s4
      dhcp4: true
```

In this configuration, two Ethernet interfaces (﻿enp0s3 and ﻿enp0s4) are configured with DHCP to obtain IP addresses. A bridge interface (﻿br0) is also configured, which combines the two Ethernet interfaces into a single logical interface. The ﻿interfaces key specifies the physical interfaces to include in the bridge.
