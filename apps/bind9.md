# Bind9

Bind9 is an open-source fully-featured DNS ([[dns]]) system. 

Project Homepage: https://www.isc.org/bind/

---
## Installation

ISC provides executables for Windows and packages for Ubuntu ([[ubuntu]]) and CentOS ([[centos]]) and Fedora ([[fedora]]) and Debian ([[debian]]) - BIND 9 ESV, Debian - BIND 9 Stable, Debian - BIND 9 Development version. Most operating systems also offer BIND 9 packages for their users. These may be built with a different set of defaults than the standard BIND 9 distribution, and some of them add a version number of their own that does not map exactly to the BIND 9 version.


### Ubuntu Linux

BIND9 is available in the Main repository. No additional repository needs to be enabled for BIND9.

```sh 
sudo apt install bind9
```


### Ubuntu Docker

As part of the [Long Term Supported OCI Images](https://ubuntu.com/security/docker-images), Canonical offers Bind9 as a hardened and maintained Docker Docker ([[docker]]).

```sh
docker run -d --name bind9-container -e TZ=UTC -p 30053:53 ubuntu/bind9:9.18-22.04_beta
```


---
## Configuration
