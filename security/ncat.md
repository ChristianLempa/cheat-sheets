# NCAT

## Connect mode (ncat is client) | default port is 31337

```shell
ncat <host> [<port>]
```

## Listen mode (ncat is server) | default port is 31337

```shell
ncat -l [<host>] [<port>]
```

## Transfer file (closes after one transfer)

```shell
ncat -l [<host>] [<port>] < file
```

## Transfer file (stays open for multiple transfers)

```shell
ncat -l --keep-open [<host>] [<port>] < file
```

## Receive file

```shell
ncat [<host>] [<port>] > file
```

## Brokering | allows for multiple clients to connect

```shell
ncat -l --broker [<host>] [<port>]
```

## Listen with SSL | many options, use ncat --help for full list

```shell
ncat -l --ssl [<host>] [<port>]
```

## Access control

```shell
ncat -l --allow <ip>
ncat -l --deny <ip>
```

## Proxying

```shell
ncat --proxy <proxyhost>[:<proxyport>] --proxy-type {http | socks4} <host>[<port>]
```

## Chat server | can use brokering for multi-user chat

```shell
ncat -l --chat [<host>] [<port>]
```
