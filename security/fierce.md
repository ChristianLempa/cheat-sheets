# Fierce

## To scan a domain and output to a file
```shell
fierce -dns <domain> -file <output_file>
```

## To scan a domain and specify which dnsserver to use
```shell
fierce -dns <domain> -dnsserver <server>
```

## To scan an internal ip range for a given server
```shell
fierce -range <ip-range> -dnsserver <server>
```

## To scan a domain using a given wordlist
```shell
fierce -dns <domain> -wordlist <wordlist>
```

## To scan a domain using a specified timeout and number of ip addresses to branch from all found addresses
```shell
fierce -dns <domain> -tcptimeout <# seconds> -traverse <# addresses>
```

## To scan domains from a list and search the entire class C for each found
```shell
fierce -dnsfile <file> -wide
```
