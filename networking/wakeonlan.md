# Wake On LAN (WOL)

Wake on LAN (WoL) is a network protocol that allows a device to be powered on remotely over a network connection. It works by sending a special network message, called a magic packet, to the device's MAC address, which triggers the device to power on from a low-power state. WoL is commonly used to remotely wake up computers for maintenance or to access files, among other purposes.


Some operating systems have settings that can enable or disable Wake-on-LAN for network interfaces. For example, on Linux, you can use the ﻿[ethtool](../linux/ethtool.md) command to enable Wake-on-LAN for a network interface.

Some network card drivers may have settings or options that control Wake-on-LAN behavior. You can usually find these settings in the advanced properties or settings for the network adapter in the Device Manager on Windows or with the ﻿[ethtool](../linux/ethtool.md) command on Linux.

Enabling Wake-on-LAN typically involves a combination of these methods, depending on the device and operating system you are using. Once Wake-on-LAN is enabled, you can use a utility like ﻿[etherwake](../linux/etherwake.md) or ﻿`wakeonlan` to send magic packets to wake up the device remotely.

