# Active State Power Management

Active State Power Management is a power management technology used in computer systems to reduce power consumption by controlling the power state of various hardware components, such as graphics cards, network adapters, and storage controllers. It helps to reduce power consumption and improve energy efficiency in these devices.

ASPM is typically enabled by default in modern computer systems. However, it can be manually enabled or disabled through the system BIOS or UEFI firmware settings. The specific steps to access and modify these settings will vary depending on the manufacturer and model of the system.

---
## How to use ASPM

If you suspect that ASPM is causing issues on your system, you can try disabling it temporarily to see if the issue goes away. To do this, you can add the `pcie_aspm=off` kernel parameter to your boot options.

1. Edit the GRUB configuration file `/etc/default/grub` with a text editor such as `nano` or `vi`.

```
$ sudo nano /etc/default/grub
```

2. Find the line that starts with `GRUB_CMDLINE_LINUX_DEFAULT` and add the `pcie_aspm=off` kernel parameter to the existing parameters between the quotes. For example:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"
```

3. Save the file and exit the text editor.

4. Update the GRUB configuration by running the following command:

```
$ sudo update-grub
```

5. Reboot your system for the changes to take effect.

After disabling ASPM, you can use the `lspci -vv` command to check if the ASPM settings have been disabled for your devices. If you still experience issues, you may need to investigate further or seek assistance from a qualified technician.

---
## ASPM Force

> **Warning:** Forcing ASPM can cause system instability or decreased performance if not done correctly. You should only force ASPM if you have a specific reason to do so and have thoroughly tested the system to ensure that it is stable and performing as expected.

That being said, if you have a specific reason to force ASPM and have thoroughly tested the system, you can use the following steps to force ASPM on a Linux system:

Add the ﻿`pcie_aspm=force` kernel parameter to the existing parameters between the quotes. For example:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"
```

