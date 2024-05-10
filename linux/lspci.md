# LSPCI Cheat-Sheet

| Command | Description |
| --- | --- |
| `lspci` | List all PCI devices in the system. |
| `lspci -v` | List all PCI devices in the system with verbose output, including vendor and device IDs, subsystem IDs, and more. |
| `lspci -vv` | List all PCI devices in the system with very verbose output, including device capabilities, IRQ settings, and ASPM (Active State Power Management) settings. |
| `lspci -s <bus_address>` | Display information for a specific PCI device with the specified bus address. |
| `lspci -k` | Show kernel driver in use for each device. |
| `lspci -n` | Show numeric IDs for vendor and device instead of names. |
| `lspci -nn` | Show numeric IDs for vendor, device, subsystem vendor, and subsystem device instead of names. |
| `lspci -t` | Display a tree-like diagram of the PCI bus hierarchy. |
| `lspci -D` | Show only PCI devices that are not behind a bridge. |
| `lspci -H1` | Show device numbers in hexadecimal format instead of decimal. |
| `lspci -x` | Show hex dump of the PCI configuration space for each device. |
