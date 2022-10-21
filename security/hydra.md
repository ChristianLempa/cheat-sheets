# Hydra

Hydra does not have a native default wordlist, using the Rockyou list is suggested

## Example brute force crack on ftp server

```shell
hydra -t 1 -l admin -P [path to password.lst] -vV [IPaddress] ftp
```

```text
--> -t # = preform # tasks
--> -l NAME = try to log in with NAME
--> -P [filepath] = Try password
--> -vV = verbose mode, showing the login+pass for each attempt
```

Check for joe accounts by adding modifier `-e s`

To write found `login+pass` combinations to field, add modifier `-0 [fileanme]`
