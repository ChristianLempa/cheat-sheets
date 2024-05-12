# PowerShell Cheat-Sheet

## File Management

| Command | Description |
| --- | --- |
| `Get-ChildItem` | List files and directories |
| `Get-Content <file>` | Get the content of a file |
| `Set-Content <file> <content>` | Set the content of a file |
| `New-Item <file>` | Create a new file |
| `New-Item <directory> -ItemType Directory` | Create a new directory |
| `Remove-Item <file>` | Remove a file |
| `Remove-Item <directory> -Recurse` | Remove a directory |
| `Rename-Item <file> <new_file>` | Rename a file or directory |
| `Copy-Item SOURCE DEST` | Copy a file |
| `Copy-Item SOURCE DEST -Recurse` | Copy a directory |
| `Move-Item SOURCE DEST` | Move a file or directory |

## Process Management

| Command | Description |
| --- | --- |
| `Get-Process` | List running processes |
| `Stop-Process -Name <process>` | Stop a process |
| `Start-Process <process>` | Start a new process |
| `Wait-Process -Name <process>` | Wait for a process to finish |

## Service Management

| Command | Description |
| --- | --- |
| `Get-Service` | List services |
| `Start-Service <service>` | Start a service |
| `Stop-Service <service>` | Stop a service |
| `Restart-Service <service>` | Restart a service |
| `Set-Service <service> -StartupType Automatic` | Set a service to start automatically |
| `Set-Service <service> -StartupType Manual` | Set a service to start manually |
| `Set-Service <service> -StartupType Disabled` | Disable a service |

## User Management

| Command | Description |
| --- | --- |
| `Get-LocalUser` | List local users |
| `New-LocalUser <user>` | Create a new local user |
| `Remove-LocalUser <user>` | Remove a local user |
| `Set-LocalUser <user> -Password <password>` | Set the password for a local user |
| `Add-LocalGroupMember -Group Administrators -Member <user>` | Add a user to the Administrators group |
| `Remove-LocalGroupMember -Group Administrators -Member <user>` | Remove a user from the Administrators group |

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
| `Install-WindowsFeature <feature>` | Install a Windows feature |
| `Uninstall-WindowsFeature <feature>` | Uninstall a Windows feature |

## Connect to a remote computer

| Command | Description |
| --- | --- |
| `Enter-PSSession -ComputerName <name> -Credential <user>` | Open a new remote session |
| `Exit-PSSession` | Close the current remote session |
| `Invoke-Command -ComputerName <name> -ScriptBlock { <command> }` | Run a command on a remote computer |
| `Invoke-Command -ComputerName <name> -FilePath <script>` | Run a script on a remote computer |
