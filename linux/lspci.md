# LSPCI

**Lspci** is a command-line utility in Linux and Unix operating systems that is used to display information about all the [PCI](../hardware/pci.md) (Peripheral Component Interconnect) buses and devices connected to the system. It provides detailed information about the hardware components, including their vendor and device IDs, subsystems, and other attributes. The **lspci** command is often used for diagnosing hardware-related issues and identifying the specific hardware components installed in a system.

---
## How to use LSPCI

Here is an example of using the ﻿**lspci** command in a Linux terminal:

```sh
$ lspci
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Desktop)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
00:14.2 Signal processing controller: Intel Corporation 200 Series PCH Thermal Subsystem
...
```

This output shows information about various hardware components in the system, including the vendor and device IDs, the device type, and the revision number.


### Show details about devices

To show detailed information about a specific device using ﻿**lspci**, you can specify the device’s bus address using the ﻿`lspci -s` option.

```sh
$ lspci -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Desktop) (rev 02)
        Subsystem: ASRock Incorporation Device 3977
        Flags: bus master, fast devsel, latency 0, IRQ 131
        Memory at a0000000 (64-bit, non-prefetchable) [size=16M]
        Memory at 90000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915
```

This output shows detailed information about the VGA compatible controller, including its subsystem, memory addresses, I/O ports, and kernel driver.


### Verbose output of lspci

The ﻿`-v` (verbose) and ﻿`-vv` (very verbose) parameters in ﻿**lspci** are used to increase the level of detail in the output.

• The ﻿`-v` option provides additional information about the devices, including the vendor and device IDs, subsystem IDs, and more.
• The ﻿`-vv` option provides even more detailed information, including the device’s capabilities, IRQ settings, and ASPM (Active State Power Management) settings.

For example, to show the [ASPM](../hardware/aspm.md) settings for the [PCI Express](../hardware/pci-express.md) device with bus address ﻿00:1c.0, you can run the following command:

```sh
$ lspci -s 00:1c.0 -vv | grep -i aspm
                ASPM L1 Enabled; L0s Enabled
```

---
## Most useful commands

| Command | Description |
| ------- | ----------- |
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

