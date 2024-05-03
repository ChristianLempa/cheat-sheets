# ARP in Linux

| Command | Description |
| --- | --- |
| `arp` | View the ARP table |
| `arp -a` | View the ARP table |
| `arp -n` | View the ARP table (don't resolve names) |
| `arp -d IP_ADDRESS` | Delete an entry from the ARP table |
| `arp -s IP_ADDRESS MAC_ADDRESS` | Add an entry to the ARP table |
| `arp -i INTERFACE -s IP_ADDRESS MAC_ADDRESS` | Add an entry to the ARP table for a specific interface |
| `arp -i INTERFACE -d IP_ADDRESS` | Delete an entry from the ARP table for a specific interface |
| `arp -i INTERFACE -n` | View the ARP table for a specific interface |
| `arp -i INTERFACE -a` | View the ARP table for a specific interface |
| `ip neigh show` | View the ARP table |
| `ip neigh show IP_ADDRESS` | View the ARP table for a specific IP address |
| `ip neigh add IP_ADDRESS lladdr MAC_ADDRESS dev INTERFACE` | Add an entry to the ARP table |
| `ip neigh change IP_ADDRESS lladdr MAC_ADDRESS dev INTERFACE` | Change an entry in the ARP table |
| `ip neigh del IP_ADDRESS dev INTERFACE` | Delete an entry from the ARP table |
| `ip neigh flush dev INTERFACE` | Flush the ARP table for a specific interface |
| `ip neigh flush all` | Flush the ARP table |
| `ip -s neigh show` | Show ARP statistics |
| `ip -s neigh flush all` | Flush the ARP cache |
