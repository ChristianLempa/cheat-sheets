# Ubuntu

Ubuntu is a Linux distribution based on Debian and composed mostly of free and open-source software.Ubuntu is officially released in three editions: Desktop, Server, and Core for Internet of things devices and robots. Ubuntu is a popular operating system for cloud computing, with support for OpenStack.

## How to enable sudo without a password for a user

Open a Terminal window and type:

```
sudo visudo
```

In the bottom of the file, add the following line:

```
$USER ALL=(ALL) NOPASSWD: ALL
```

Where `$USER` is your username on your system. Save and close the sudoers file (if you haven't changed your default terminal editor (you'll know if you have), press Ctl + x to exit `nano` and it'll prompt you to save).

---
## Networking

In Ubuntu, networking can be managed using various tools and utilities, including the following:

1. **NetworkManager**: NetworkManager is a system service that manages network connections and devices. It provides a graphical user interface (GUI) for configuring network settings, as well as a command-line interface (CLI) for advanced configuration. NetworkManager is the default network management tool in Ubuntu.

2. **Netplan**: [Netplan](../netplan) is a command-line utility for configuring network interfaces in modern versions of Ubuntu. It uses YAML configuration files to describe network interfaces, IP addresses, routes, and other network-related parameters. [Netplan](../netplan) generates the corresponding configuration files for the underlying network configuration subsystem, such as systemd-networkd or NetworkManager.

3. **ifupdown**: ifupdown is a traditional command-line tool for managing network interfaces in Ubuntu. It uses configuration files located in the ﻿/etc/network/ directory to configure network interfaces, IP addresses, routes, and other network-related parameters.

To manage networking in **Ubuntu**, you can use one or more of these tools depending on your needs and preferences. For example, you can use the NetworkManager GUI to configure basic network settings and use [Netplan](../netplan) or ifupdown for advanced configuration. You can also use the command-line tools to automate network configuration tasks or to configure networking on headless servers.
