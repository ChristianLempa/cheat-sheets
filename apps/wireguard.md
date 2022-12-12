# WireGuard
WireGuard® is an extremely simple yet fast and modern **VPN ([[vpn]])** that utilizes state-of-the-art. It aims to be faster, simpler, leaner, and more useful than IPsec, while avoiding the massive headache. It intends to be considerably more performant than OpenVPN. WireGuard is designed as a general purpose VPN for running on embedded interfaces and super computers alike, fit for many different circumstances.

---
#### Create Wireguard keys (private & publickey)

```
wg genkey | tee privatekey | wg pubkey > publickey
```

#### Example of server config

for example:
```
nano /etc/wireguard/wg0.conf
```

Example server config:
```
[Interface]
Address = 192.168.8.1/0 #ip of the wireguard server
SaveConfig = true
ListenPort = 51820 # default port you can change it
FwMark = 0xca6c
PrivateKey = #paste here your privatekey

PostUp = iptables -A FORWARD -i wg0 -j ACCEPT
PostUp = iptables -t nat -A POSTROUTING -o ens2 -j MASQUERADE
PostDown = iptables -A FORWARD -i wg0 -j ACCEPT
PostDown= iptables -t nat -A POSTROUTING -o ens2 -j MASQUERADE

# change here your peers conf
[Peer]
PublicKey = #paste here your pub key of your client
AllowedIPs = 192.168.8.3/32 # change ip in your range
PersistentKeepalive = 25

[Peer]
PublicKey = #paste here your pub key of your client
AllowedIPs = 192.168.8.2/32 # change ip in your range
PersistentKeepalive = 25
```

#### Example of the client config

```
[Interface]
Address = 192.168.8.2/32 # change this to the ip that you want for your client
MTU = 1420
SaveConfig = true
ListenPort = 47991
FwMark = 0xca6c
PrivateKey = # set here the privatekey of your client.

[Peer]
PublicKey = # paste here the public key of your wireguard server
AllowedIPs = 0.0.0.0/0
Endpoint = your-external-ip:51820
PersistentKeepalive = 15

```









## Troubleshooting

With this command you can enable the debug logging in WireGuard:

```bash
echo 'module wireguard +p' | sudo tee /sys/kernel/debug/dynamic_debug/control
```

And the same command with -p can disable it again:

```bash
echo 'module wireguard -p' | sudo tee /sys/kernel/debug/dynamic_debug/control
```