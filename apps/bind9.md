# Bind9

Bind9 is an open-source fully-featured [DNS](networking/dns) system. 

Project Homepage: https://www.isc.org/bind/

---
## Installation

ISC provides executables for Windows and packages for [Ubuntu](linux/distros/ubuntu.md), [CentOS](linux/distros/centos.md), [Fedora](linux/distros/fedora.md)  and [Debian](linux/distros/debian.md) - BIND 9 ESV, Debian - BIND 9 Stable, Debian - BIND 9 Development version. Most operating systems also offer BIND 9 packages for their users. These may be built with a different set of defaults than the standard BIND 9 distribution, and some of them add a version number of their own that does not map exactly to the BIND 9 version.


### Ubuntu Linux

BIND9 is available in the Main repository. No additional repository needs to be enabled for BIND9.

```sh 
sudo apt install bind9
```


### Ubuntu Docker

As part of the [Long Term Supported OCI Images](https://ubuntu.com/security/docker-images), Canonical offers Bind9 as a hardened and maintained [Docker](docker/docker.md).

```sh
docker run -d --name bind9-container -e TZ=UTC -p 30053:53 ubuntu/bind9:9.18-22.04_beta
```


---
## Configuration

BIND 9 uses a single configuration file called `named.conf`, which is typically located in either `/etc/bind`, `/etc/namedb` or `/usr/local/etc/namedb`.

The `named.conf` consists of `logging`, and `options` blocks, and `category`, `channel`, `directory`, `file` and `severity` statements.

### Named Config

```conf
options {
	...
};

zone "domain.tld" {
	type primary;
	file "domain.tld";
};
```

### Zone File

Depending on the functionality of the system, one or more `zone` files is required.

```conf
; base zone file for domain.tld
$TTL 2d    ; default TTL for zone

$ORIGIN domain.tld. ; base domain-name

; Start of Authority RR defining the key characteristics of the zone (domain)
@         IN      SOA   ns1.domain.tld. hostmaster.domain.tld. (
                                2022121200 ; serial number
                                12h        ; refresh
                                15m        ; update retry
                                3w         ; expiry
                                2h         ; minimum
                                )

; name server RR for the domain
           IN      NS      ns1.domain.tld.

; mail server RRs for the zone (domain)
        3w IN      MX  10  mail.domain.tld.

; domain hosts includes NS and MX records defined above
; plus any others required
; for instance a user query for the A RR of joe.domain.tld will
; return the IPv4 address 192.168.254.6 from this zone file
ns1        IN      A       192.168.254.2
mail       IN      A       192.168.254.4
joe        IN      A       192.168.254.6
www        IN      A       192.168.254.7

```

#### SOA (Start of Authority)

A start of authority record is a type of resource record in the Domain Name System ([DNS](networking/dns.md)) containing administrative information about the zone, especially regarding zone transfers. The SOA record format is specified in RFC 1035.

```conf
@         IN      SOA   ns1.domain.tld. hostmaster.domain.tld. (
                                2022121200 ; serial number
                                12h        ; refresh
                                15m        ; update retry
                                3w         ; expiry
                                2h         ; minimum
                                )
```

