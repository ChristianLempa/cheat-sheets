# NMAP

## HTB scan
### sV: enumerate versions
### sC: safe script
### oA: output all formats

```shell
nmap -sV -sC -oA nmap 0.0.0.0
```

## Nmap verbose scan, runs syn stealth, T4 timing (should be ok on LAN), OS and service version info, traceroute and scripts against services

```shell
nmap -v -sS -A -T4 target
```

## As above but scans all TCP ports (takes a lot longer)

```shell
nmap -v -sS -p- -A -T4 target
```

## As above but scans all TCP ports and UDP scan (takes even longer)

```shell
nmap -v -sU -sS -p- -A -T4 target
```

## Search nmap scripts for keywords
ls /usr/share/nmap/scripts/* | grep ftp

## Nmap script to scan for vulnerable SMB servers - WARNING: unsafe=1 may cause knockover

```shell
nmap -v -p 445 --script=smb-check-vulns --script-args=unsafe=1 target
```

## Port 21 - FTP

```shell
nmap --script ftp-anon,ftp-bounce,ftp-libopie,ftp-proftpd-backdoor,ftp-vsftpd-backdoor,ftp-vuln-cve2010-4221,tftp-enum -p 21 target
```

## Port 25 - SMTP

```shell
nmap --script=smtp-commands,smtp-enum-users,smtp-vuln-cve2010-4344,smtp-vuln-cve2011-1720,smtp-vuln-cve2011-1764 -p 25 target
smtp-user-enum -M VRFY -U /root/sectools/SecLists/Usernames/Names/names.txt -t target
```

## Port 69 - UDP - TFTP

```shell
nmap -p69 --script=tftp-enum.nse 10.11.1.111
```

## Port 88 - Kerberos

```shell
nmap -p 88 --script=krb5-enum-users --script-args="krb5-enum-users.realm='DOMAIN.LOCAL'" Target
```

## Port 135 - MSRPC

```shell
nmap target --script=msrpc-enum
```

## Port 139/445 - SMB

```shell
nmap --script=smb-enum* --script-args=unsafe=1 -T5 target
nmap --script smb-enum-shares -p139,445 -T4 -Pn targer
nmap --script smb-vuln* -p139,445 -T4 -Pn target
nmap -p445 --script smb-brute --script-args userdb=userfilehere,passdb=/usr/share/seclists/Passwords/Common-Credentials/10-million-password-list-top-1000000.txt target  -vvvv
nmap –script smb-brute target
```

## Port 161/162 UDP - SNMP

```shell
nmap -vv -sV -sU -Pn -p 161,162 --script=snmp-netstat,snmp-processes target
```

## Port 443 - HTTPS

```shell
nmap -sV --script=ssl-heartbleed target
```

## Port 1433 - MSSQL

```shell
nmap -p 1433 -sU --script=ms-sql-info.nse target
```

## Port 1521 - Oracle

```shell
nmap -p 1521 -A target
nmap -p 1521 --script=oracle-tns-version,oracle-sid-brute,oracle-brute target
```

## Port 3306 - MySQL

```shell
nmap --script=mysql-databases.nse,mysql-empty-password.nse,mysql-enum.nse,mysql-info.nse,mysql-variables.nse,mysql-vuln-cve2012-2122.nse target -p 3306
```

## Port 3389 - RDP

```shell
nmap -p 3389 --script=rdp-vuln-ms12-020.nse target
```

## Port 5900 - VNC

```shell
nmap --script=vnc-info,vnc-brute,vnc-title -p 5900 target
```
