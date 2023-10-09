# ARP in Linux

The **arp** command in Linux allows you to view and modify the [ARP table](../networking/arp-protocol.md), which contains information about devices on the local network. It can be used to view the IP addresses and MAC addresses of devices on the network, and to add or remove entries from the [ARP table](../networking/arp-protocol.md).

| Command | Description |
| --- | --- |
| `arp` | View the ARP table |
| `arp -a` | View the ARP table |
| `arp -n` | View the ARP table (don't resolve names) |
| `arp -d <ip-address>` | Delete an entry from the ARP table |
| `arp -s <ip-address> <mac-address>` | Add an entry to the ARP table |
