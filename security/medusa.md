# Medusa

## Display all currently installed modules

```shell
medusa -d
```

## Display specific options for a module

```shell
medusa -M [module_name] -q
```

## Test all passwords in password file against the admin user on the host
### 192.168.1.20 via the SMB | SSH | MySQL | HTTP service 

```shell
medusa -h 192.168.1.20 -u admin -P passwords.txt -M [smbnt | ssh | mssql | http]
```

## Brute force 10 hosts and 5 users concurrently (using Medusa's parallel features)
### Each of the 5 threads targeting a host will check a specific user

```shell
medusa -H hosts.txt -U users.txt -P passwords.txt -T 10 -t 5 -L -F -M smbnt
```


Medusa allows username, password, and host data to be placed within the same file (the "combo" file).

Possible combinations in the combo file:

```text
# host:username:password
# host:username:
# host::
# :username:password
# :username:
# ::password
# host::password
# :id:lm:ntlm::: (PwDump files)
```

## Test each username/password entry in the file combo.txt

```shell
medusa -M smbnt -C combo.txt
```
