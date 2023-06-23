# Ethtool


## Enable Wake On LAN (WoL) on the network adapter

Use the following command to check if your network interface supports WoL:

```sh
sudo ethtool <interface_name> | grep "Wake-on"
```

If the output shows "Wake-on: d", it means that WoL is disabled.

To enable WoL, use the following command:

```sh
sudo ethtool -s <interface_name> wol g
```

To make the WoL setting persistent across reboots, add the following line to the `/eth/network/interfaces` file:

```sh
post-up /usr/sbin/ethtool -s <interface_name> wol g
```

