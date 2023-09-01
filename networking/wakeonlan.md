# Wake On LAN (WOL)

**Wake on LAN (WoL)** is a network protocol that allows a device to be powered on remotely over a network connection. It works by sending a special network message, called a magic packet, to the device's MAC address, which triggers the device to power on from a low-power state. **Wake on LAN (WoL)** is commonly used to remotely wake up computers for maintenance or to access files, among other purposes.

## Using Wake on LAN (WoL)

Some operating systems have settings that can enable or disable **Wake on LAN (WoL)** for network interfaces. For example, on [Linux](../linux/linux.md), you can use the [ethtool](../linux/ethtool.md) command to enable **Wake on LAN (WoL)** for a network interface.

Some network card drivers may have settings or options that control **Wake on LAN (WoL)** behavior. You can usually find these settings in the advanced properties or settings for the network adapter in the Device Manager on Windows or with the [ethtool](../linux/ethtool.md) command on [Linux](../linux/linux.md).

### Enabling Wake on LAN (WoL)

Enabling **Wake on LAN (WoL)** typically involves a combination of these methods, depending on the device and operating system you are using. Once **Wake on LAN (WoL)** is enabled, you can use a utility like [etherwake](../linux/etherwake.md) or `wakeonlan` to send magic packets to wake up the device remotely.

## Troubleshooting

If you are having trouble getting **Wake on LAN (WoL)** to work, here are some things you can try:

1. Make sure that **Wake on LAN (WoL)** is enabled in the BIOS or UEFI settings of the device you are trying to wake up.
2. Make sure that **Wake on LAN (WoL)** is enabled for the network interface on the device you are trying to wake up.
3. Make sure that the network interface is connected to a network that is configured to allow **Wake on LAN (WoL)**.

If you're still not able to get **Wake on LAN (WoL)** to work, you can try using a different utility to send the magic packet. For example, if you're using [etherwake](../linux/etherwake.md), you can try using `wakeonlan` instead.

### Capturing Wake on LAN (WoL) packets

If you're having trouble getting **Wake on LAN (WoL)** to work, you can try capturing the magic packet with a packet sniffer like [Wireshark](../tools/wireshark.md), or [TcpDump](../tools/tcpdump.md) to see if it is being sent correctly. If you don't see any packets being sent, then there may be a problem with the network interface or network configuration.

```sh
tcpdump -ni any ether proto 0x0842 or udp port 9 2>/dev/null
```

This is an example packet.

```sh
16:19:27.965101 enp3s0 Out IP 10.50.0.19.43610 > 10.50.0.5.9: UDP, length 102
```
