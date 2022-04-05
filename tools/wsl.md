# WSL Cheat-Sheet

## Networking
### Port Forwarding
**Find IP Address**
```powershell
bash.exe -c "ifconfig eth0 | grep 'inet '"
```

**Add PortForwarding**
```powershell
$port = 8080
$remoteaddr = 0.0.0.0

netsh interface portproxy add v4tov4 listenport=$port connectport=$port connectaddress=$remoteaddr

netsh advfirewall firewall add rule name=$port dir=in action=allow protocol=TCP localport=$port
```

**Delete PortForwarding**
```PowerShell
$port = 8080

netsh interface portproxy delete v4tov4 listenport=$port
netsh advfirewall firewall delete rule name=$port

```

**Show PortForwardings**
```powershell
netsh interface portproxy show v4tov4
```
