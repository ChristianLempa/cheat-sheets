# Environment Variables in Windows

## How to use them in PowerShell
Environment Varaibles can be used in [PowerShell](windows/powershell.md) with the prefix `$env:`.

**Example***:
*Variable:*  `%APPDATA%`
*In Powershell:* `$env:APPDATA`

## List of environment variables
Variable | Description
---|---
`%ALLUSERSPROFILE%`|C:\ProgramData
`%APPDATA%`|C:\Users\{username}\AppData\Roaming
`%COMMONPROGRAMFILES%`|C:\Program Files\Common Files
`%COMMONPROGRAMFILES(x86)%`|C:\Program Files (x86)\Common Files
`%CommonProgramW6432%`|C:\Program Files\Common Files
`%COMSPEC%`|C:\Windows\System32\cmd.exe
`%HOMEDRIVE%`|C:\
`%HOMEPATH%`|C:\Users\{username}
`%LOCALAPPDATA%`|C:\Users\{username}\AppData\Local
`%LOGONSERVER%`|\\{domain_logon_server}
`%PATH%`|C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem
`%PathExt%`|.com;.exe;.bat;.cmd;.vbs;.vbe;.js;.jse;.wsf;.wsh;.msc
`%PROGRAMDATA%`|C:\ProgramData
`%PROGRAMFILES%`|C:\Program Files
`%ProgramW6432%`|C:\Program Files
`%PROGRAMFILES(X86)%`|C:\Program Files (x86)
`%PROMPT%`|$P$G
`%SystemDrive%`|C:
`%SystemRoot%`|C:\Windows
`%TEMP%`|C:\Users\{username}\AppData\Local\Temp
`%TMP%`|C:\Users\{username}\AppData\Local\Temp
`%USERDOMAIN%`|Userdomain associated with current user.
`%USERDOMAIN_ROAMINGPROFILE%`|Userdomain associated with roaming profile.
`%USERNAME%`|{username}
`%USERPROFILE%`|C:\Users\{username}
`%WINDIR%`|C:\Windows
`%PUBLIC%`|C:\Users\Public
`%PSModulePath%`|%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\
`%OneDrive%`|C:\Users\{username}\OneDrive
`%DriverData%`|C:\Windows\System32\Drivers\DriverData
`%CD%`|Outputs current directory path. (Command Prompt.)
`%CMDCMDLINE%`|Outputs command line used to launch current Command Prompt session. (Command Prompt.)
`%CMDEXTVERSION%`|Outputs the number of current command processor extensions. (Command Prompt.)
`%COMPUTERNAME%`|Outputs the system name.
`%DATE%`|Outputs current date. (Command Prompt.)
`%TIME%`|Outputs time. (Command Prompt.)
`%ERRORLEVEL%`|Outputs the number of defining exit status of previous command. (Command Prompt.)
`%PROCESSOR_IDENTIFIER%`|Outputs processor identifier.
`%PROCESSOR_LEVEL%`|Outputs processor level.
`%PROCESSOR_REVISION%`|Outputs processor revision.
`%NUMBER_OF_PROCESSORS%`|Outputs the number of physical and virtual cores.
`%RANDOM%`|Outputs random number from 0 through 32767.
`%OS%`|Windows_NT
