# WireGuard
WireGuard® is an extremely simple yet fast and modern **VPN ([[vpn]])** that utilizes state-of-the-art. It aims to be faster, simpler, leaner, and more useful than IPsec, while avoiding the massive headache. It intends to be considerably more performant than OpenVPN. WireGuard is designed as a general purpose VPN for running on embedded interfaces and super computers alike, fit for many different circumstances.

---
## Troubleshooting

With this command you can enable the debug logging in WireGuard:

```bash
echo 'module wireguard +p' | sudo tee /sys/kernel/debug/dynamic_debug/control
```

And the same command with -p can disable it again:

```bash
echo 'module wireguard -p' | sudo tee /sys/kernel/debug/dynamic_debug/control
```