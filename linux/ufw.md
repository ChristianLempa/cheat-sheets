# UFW (uncomplicated firewall)

UFW (uncomplicated firewall) is a firewall configuration tool for **[Linux](linux.md)** that runs on top of [IPTables](iptables.md), included by default within Ubuntu distributions. It provides a streamlined interface for configuring common firewall use cases via the command line.

## Enable UFW

To check if ufw is enabled, run:
```bash
sudo ufw status
```

To enable UFW on your system, run:
```bash
sudo ufw enable
```

If for some reason you need to disable UFW, you can do so with the following command:
```bash
sudo ufw disable
```

Block an IP Address

## Block an IP Address/Subnet

```bash
sudo ufw deny from 203.0.113.0/24
```

