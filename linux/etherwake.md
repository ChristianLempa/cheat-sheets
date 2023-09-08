# Etherwake

Etherwake is a command-line utility for sending [Wake-on-LAN (WoL)](../networking/wakeonlan.md) magic packets to wake up a device over a network connection. It allows you to wake up a device by specifying its MAC address as an argument, and it sends the magic packet to the broadcast address of the network interface that is specified.

Here's an example of how to use ﻿Etherwake to wake up a device with a specific MAC address:

```sh
sudo etherwake -i eth0 00:11:22:33:44:55
```

In this example, `sudo` is used to run the command with administrative privileges, `-i eth0` specifies the network interface to use (in this case, `eth0`), and `00:11:22:33:44:55` is the MAC address of the device to wake up.

The command sends a Wake-on-LAN magic packet to the broadcast address of the `eth0` network interface, which should wake up the device with the specified MAC address if Wake-on-LAN is enabled on the device.

Note that the exact syntax and options for `etherwake` may vary depending on your operating system and version of the utility. You can usually find more information and examples in the `etherwake` manual page (`man etherwake`).
