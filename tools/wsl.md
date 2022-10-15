# WSL Cheat-Sheet
## Backup and Restore WSL
### Backup a WSL Distro
```powershell
wsl --export (distribution) (filename.tar)
```
### Restore a WSL Distro from Backup
```powershell
wsl --import (distribution) (install location) (file location and filename)
```

## Symbolic Links
### Link .ssh folder
```bash
sudo ln -s /mnt/c/Users/lempa/.ssh ~/.ssh
```

### Link .kube folder
```bash
sudo ln -s /mnt/c/Users/lempa/.ssh ~/.ssh
```

## File Permissions
Advanced settings configuration in WSL: [WSL Config Parameters](https://docs.microsoft.com/en-us/windows/wsl/wsl-config)

**Example wsl.conf**
```
[automount]
enabled = true
options = "metadata,uid=1000,gid=1000,umask=077,fmask=11,case=off"
mountFsTab = true

[interop]
enabled = false
appendWindowsPath = false
```

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
