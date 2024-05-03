# PowerShell Cheat-Sheet

## File Management

| Command | Description |
| --- | --- |
| `Get-ChildItem` | List files and directories |
| `Get-Content FILE` | Get the content of a file |
| `Set-Content FILE CONTENT` | Set the content of a file |
| `New-Item FILE` | Create a new file |
| `New-Item DIR -ItemType Directory` | Create a new directory |
| `Remove-Item FILE` | Remove a file |
| `Remove-Item DIR -Recurse` | Remove a directory |
| `Rename-Item OLDNAME NEWNAME` | Rename a file or directory |
| `Copy-Item SOURCE DEST` | Copy a file |
| `Copy-Item SOURCE DEST -Recurse` | Copy a directory |
| `Move-Item SOURCE DEST` | Move a file or directory |

## Process Management

| Command | Description |
| --- | --- |
| `Get-Process` | List running processes |
| `Stop-Process -Name PROCESS` | Stop a process |
| `Start-Process PROGRAM` | Start a new process |
| `Wait-Process -Name PROCESS` | Wait for a process to finish |

## Service Management

| Command | Description |
| --- | --- |
| `Get-Service` | List services |
| `Start-Service SERVICE` | Start a service |
| `Stop-Service SERVICE` | Stop a service |
| `Restart-Service SERVICE` | Restart a service |
| `Set-Service SERVICE -StartupType Automatic` | Set a service to start automatically |
| `Set-Service SERVICE -StartupType Manual` | Set a service to start manually |
| `Set-Service SERVICE -StartupType Disabled` | Disable a service |

## User Management

| Command | Description |
| --- | --- |
| `Get-LocalUser` | List local users |
| `New-LocalUser USERNAME` | Create a new local user |
| `Remove-LocalUser USERNAME` | Remove a local user |
| `Set-LocalUser USERNAME -Password PASSWORD` | Set the password for a local user |
| `Add-LocalGroupMember -Group Administrators -Member USERNAME` | Add a user to the Administrators group |
| `Remove-LocalGroupMember -Group Administrators -Member USERNAME` | Remove a user from the Administrators group |

## Network Management

| Command | Description |
| --- | --- |
| `Get-NetIPAddress` | List IP addresses |
| `Get-NetAdapter` | List network adapters |

## Windows Updates

| Command | Description |
| --- | --- |
| `Install-Module -Name PSWindowsUpdate` | Install the PSWindowsUpdate module |
| `Get-Command -Module PSWindowsUpdate` | List all commands in the PSWindowsUpdate module |
| `Get-WUInstall` | Install Windows updates |

## Windows Features

| Command | Description |
| --- | --- |
| `Get-WindowsFeature` | List Windows features |
| `Install-WindowsFeature FEATURE` | Install a Windows feature |
| `Uninstall-WindowsFeature FEATURE` | Uninstall a Windows feature |

## Connect to a remote computer

| Command | Description |
| --- | --- |
| `Enter-PSSession -ComputerName SERVER -Credential USERNAME` | Open a new remote session |
| `Exit-PSSession` | Close the current remote session |
| `Invoke-Command -ComputerName SERVER -ScriptBlock { COMMAND }` | Run a command on a remote computer |
| `Invoke-Command -ComputerName SERVER -FilePath SCRIPT.ps1` | Run a script on a remote computer |
