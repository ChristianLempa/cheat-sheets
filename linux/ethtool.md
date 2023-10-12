# Ethtool

**Ethtool** is a command-line utility used in [Linux](../linux/linux.md) systems to query and control network interface settings. It provides information about the network interface cards (NICs) installed on a system, such as link status, driver information, speed, duplex mode, and more, and allows you to modify certain settings of a network interface.

## Using Ethtool to view network interface information

To view general information about a specific network interface (e.g., eth0), use the following command:

```sh
ethtool interface_name
```

If you want to retrieve only the link status of an interface, you can use the ﻿-i option followed by the interface name:

```sh
ethtool -i interface_name
```

## Using Ethtool to change network interface settings

**Ethtool** allows you to modify certain settings of a network interface. For example, you can manually set the speed and duplex mode, enable or disable features like [Wake-on-LAN](../networking/wakeonlan.md) or [autonegotiation](../networking/autonegotiation.md), configure flow control settings, and adjust ring buffer sizes.

### Manually set the speed and duplex mode of a network interface

To manually set the speed and duplex mode of a network interface (e.g., eth0) to a specific value, use the following command:

```sh
ethtool -s interface_name speed interface_speed duplex interface_duplex
```

If you want to enable or disable autonegotiation on a specific interface, you can use the following command:

```sh
ethtool -s interface_name autoneg on
ethtool -s interface_name autoneg off
```

### Enable Wake On LAN (WoL) on the network adapter

Use the following command to check if your network interface supports Wake On LAN (WoL):

```sh
sudo ethtool interface_name | grep "Wake-on"
```

If the output shows "Wake-on: d", it means that Wake On LAN (WoL) is disabled.

To enable Wake On LAN (WoL), use the following command:

```sh
sudo ethtool -s interface_name wol g
```

### Make the Wake On LAN (WoL) setting persistent across reboots

To make the Wake On LAN (WoL) setting persistent across reboots, add the following line to the `/etc/network/interfaces` file:

```sh
post-up /usr/sbin/ethtool -s interface_name wol g
```
