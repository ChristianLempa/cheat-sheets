# ARP in Linux

| Command | Description |
| --- | --- |
| `arp` | View the ARP table |
| `arp -a` | View the ARP table |
| `arp -n` | View the ARP table (don't resolve names) |
| `arp -d <ip>` | Delete an entry from the ARP table |
| `arp -s <ip> <mac_address>` | Add an entry to the ARP table |
| `arp -i <interface> -s <ip> <mac_address>` | Add an entry to the ARP table for a specific interface |
| `arp -i <interface> -d <ip>` | Delete an entry from the ARP table for a specific interface |
| `arp -i <interface> -n` | View the ARP table for a specific interface |
| `arp -i <interface> -a` | View the ARP table for a specific interface |
| `ip neigh show` | View the ARP table |
| `ip neigh show <ip>` | View the ARP table for a specific IP address |
| `ip neigh add <ip> lladdr <mac_address> dev <interface>` | Add an entry to the ARP table |
| `ip neigh change <ip> lladdr <mac_address> dev <interface>` | Change an entry in the ARP table |
| `ip neigh del <ip> dev <interface>` | Delete an entry from the ARP table |
| `ip neigh flush dev <interface>` | Flush the ARP table for a specific interface |
| `ip neigh flush all` | Flush the ARP table |
| `ip -s neigh show` | Show ARP statistics |
| `ip -s neigh flush all` | Flush the ARP cache |
