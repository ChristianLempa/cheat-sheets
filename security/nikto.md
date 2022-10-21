# Nikto

## Scan a particular host

```shell
nikto -host [host IP/name]
```

## Scan a host on multiple ports (default = 80)

```shell
nikto -host [host IP/name] -port [port number 1], [port number 2], [port number 3]
```

## Scan a host and output fingerprinted information to a file

```shell
nikto -host [host IP/name] -output [output_file]
```

## Use a proxy while scanning a host 

```shell
nikto -host [host IP/name] -useproxy [proxy address]
```
