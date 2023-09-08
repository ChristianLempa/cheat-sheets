# Wake On LAN (WOL)

**Wake on LAN (WoL)** is a network protocol that allows a device to be powered on remotely over a network connection. It works by sending a special network message, called a **magic packet**, to the device's MAC address, which triggers the device to power on from a low-power state. **Wake on LAN (WoL)** is commonly used to remotely wake up computers for maintenance or to access files, among other purposes.

## Magic Packet

The **magic packet** contains the device's MAC address and a special sequence of bytes that the device recognizes as a **magic packet**. It consists of a 6-byte header followed by the repetition of the target device's MAC address 16 times, resulting in a total packet size of 102 bytes.

The **magic packet** is sent to the device's MAC address using the [UDP](../networking/udp.md) protocol on port 9. It is usually sent as a broadcast packet to the network's broadcast address, allowing it to reach all devices on the local network segment. However, it's worth noting that **Wake on LAN (WoL)** can also be sent as a unicast packet. In a unicast configuration, the **magic packet** is sent directly to the specific IP address of the target device instead of being broadcasted to all devices on the network. This requires knowing the IP address of the device in advance.

## Enabling Wake on LAN (WoL)

It's important to note that for **Wake on LAN (WoL)** to work, the target device must be properly configured to listen for and respond to the **magic packet** on the specified UDP port. Additionally, some networking equipment or firewalls might block or restrict UDP broadcasts, which could affect the successful transmission of the **magic packet**.

### Enable Wake on LAN (WoL) in BIOS or UEFI

Most modern computers have a setting in the BIOS or UEFI settings that allows you to enable or disable **Wake on LAN (WoL)** for the network interface. This setting is usually found under the **Power Management** or **Power Options** section of the BIOS or UEFI settings.

### Enable Wake on LAN (WoL) in the operating system

Some operating systems have settings that can enable or disable **Wake on LAN (WoL)** for network interfaces. For example, on [Linux](../linux/linux.md), you can use the [ethtool](../linux/ethtool.md) command to enable **Wake on LAN (WoL)** for a network interface.

## Sending Magic Packets

Once **Wake on LAN (WoL)** is enabled, you can use a utility like [etherwake](../linux/etherwake.md) or `wakeonlan` to send **magic packets** to wake up the device remotely.

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
