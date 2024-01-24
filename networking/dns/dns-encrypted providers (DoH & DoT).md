# Secure DNS options (DoH/DOT)

There are many options for implementing secure DNS including but not limited to:
 - Software level (i.e. internet browser)
 - Workstation/Host level (OS dependant - Windows, Apple, Linux)
 - Network level (LAN)

Enabling at the workstation/host level ensures that, when connecting to the internet while away from a trusted network, your queries will still be encrypted properly.  Secure DNS can also be implemented at the network level by means of an additional hardware \[or software\] name server within the LAN, or software & configuration at the network gateway. 

## Organic OS configuration

Secure DNS can be utilized organically with Apple operating systems (as of [iOS 14](https://rodneylab.com/how-to-enable-encrypted-dns-on-iphone-ios-14/) and [macOS 11](https://support.apple.com/guide/mac-help/change-dns-settings-on-mac-mh14127/mac)) and [Windows 10/11](https://www.howtogeek.com/765940/how-to-enable-dns-over-https-on-windows-11/).  Neither are enabled by default and OS-internal secure DNS requires differing levels of complexity and user intervention.  Linux OS's can be configured to use Secure DNS with one of many software DNS options.

> _Editor's Note:_ In this writer's opinion it should be preferred to implement third-party software DNS provider (especially in Windows) due to the "per-connection" nature of secure DNS configurations and the length some of these organic configurations require...  Also, who really thinks Apple & Windows have an invested interest in **enhancing** your internet privacy??

## Third-Party Software (whole-system secure DNS)

1) [Safing Portmaster](https://safing.io/) - Packet-level whole system firewall and content filter with graphical interface for configuration & monitoring.  Windows & Linux options available.  (This writer's favorite!!)
2) [Cloudflare Client Software](https://developers.cloudflare.com/1.1.1.1/setup/) - Apps available in Apple App Store & Google Play Store
3) [Unbound](https://nlnetlabs.nl/projects/unbound/about/) - A validating, recursive, caching DNS resolver. It is designed to be fast and lean and incorporates modern features based on open standards.
4) [BIND](https://www.isc.org/bind/) -  Quasi-ubiquitous DNS service provided, or otherwise available for, almost all Linux distributions, appliances, and IoT devices.  Openly developed on GitLab.  A bit more complicated to configure but highly customizable.

## Web browser internal configuration

Most popular internet browsers today can be configured to utilize secure DNS regardless of workstation/host and LAN configuration.  It's better than nothing -- but it does not protect any of the DNS queries originating from the host outside the browser!

 - [Chromium forks](https://helpdeskgeek.com/how-to/what-is-secure-dns-and-how-to-enable-it-in-google-chrome/): Chromium, Google Chrome, MS Edge, Brave, etc.
 - [Mozilla Firefox](https://support.mozilla.org/en-US/kb/dns-over-https)
 - [Opera](https://winaero.com/enable-dns-over-https-in-opera-doh/)

## Network/LAN configurations

Many routers/LAN gateways can be [organically configured](https://developers.cloudflare.com/1.1.1.1/setup/router/) to utilize secure DNS without third-party software.  Depending on desired DoH/DoT provider \[see below\] certain IP addresses or combinations will configure the DNS query configurations accordingly.

Some routers also have, or are able to install, a software DNS service such as those listed above -- even with COTS name-brand proprietary firmware (i.e. Asus, Netgear, Linksys, etc.)  More sophisticated open source software routers/firewalls (i.e. OpenWRT/DD-WRT, PFSense, OpnSense, etc.) can utilize software DNS services with graphical advanced configuration options.

>[!tip]
>If you've been reading all the way from the [[cheatsheets/networking/dns/dns|DNS]] page to find out about "AdHoles", ad filters, content filters, and security blacklists -- Congratulations!  You've reached the answer!!

Additional hardware and/or software can be added to your LAN to provide secure DNS... and most of them come with remarkable benefits: **_Content Filtering!!!_**  Blocking advertisements, inappropriate content, and potentially dangerous or malicious connections all have one thing in common -- these capabilities are rooted in filtering DNS queries.

Hardware solutions for this purpose are almost limitless but include the notorious [RaspberryPi](https://www.raspberrypi.com/), [OrangePi](http://www.orangepi.org/), many other Single Board Computers (SBCs), or any x86 or ARM architecture hardware you wish to configure as such.  Configure the network gateway with the address of one of these physical devices as the upstream DNS name server and all network traffic will be addressed through that device before exiting to the web.  Even better: if you have a DHCP server that you can set the DNS name server to your additional device... this configuration eliminates the gateway's DNS routing as a middle-man, and enables differing configurations if some of your devices don't need \[or differing levels of\] content filtering.

Lastly: secure DNS and/or content filtering software/services can be installed on other hardware, VM, or Docker/Kubernetes container within the LAN and addressed in the same way as the gateway DNS and/or DHCP DNS nameserver example above.  Two of the most well known software solutions are [AdGuard](https://adguard.com/en/welcome.html) and [PiHole](https://pi-hole.net/). 

Want redundant secure DNS name servers in case one goes down for maintenance or updates?  Combine network gateway secure DNS with an additional hardware appliance... Or combine a hardware appliance with a software service within the LAN.  Go crazy!

## Popular DoH/DoT Hosts

1) [Cloudflare](https://www.cloudflare.com/dns/)
2) [Quad9](https://www.quad9.net/)
3) [OpenDNS](https://www.opendns.com/)
4) [DNSWatch](https://dns.watch/)
5) [OpenNIC](https://www.opennic.org/)