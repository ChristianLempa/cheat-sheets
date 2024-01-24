# Domain Name Service (DNS)

[DNS (Domain Name System)](https://en.wikipedia.org/wiki/Domain_Name_System) is a hierarchical distributed naming system used to translate human-readable domain names, such as `www.example.com`, into [[IP]] (Internet Protocol) addresses, such as 192.0.2.1, that computers use to identify each other on the Internet. DNS allows users to access websites and other Internet resources using easy-to-remember domain names instead of having to remember the numerical IP addresses that correspond to them.

## How DNS works

DNS operates using a client-server architecture. When a user types a domain name into their web browser, the browser sends a DNS query to a DNS resolver, which is typically provided by the user’s Internet Service Provider (ISP). The resolver then sends a series of recursive queries to other DNS servers, working its way up the DNS hierarchy until it receives a response containing the IP address associated with the requested domain name.

>[!info]
>Hey: what's the deal with all the big tech talk of "AdHoles", ad filters, content filters, and security blacklists all about?  Surprise: It's all about DNS!  Read on to see how...

## DNS Structure

DNS is organized into a hierarchical structure of domains, with the root zones (also known as a "Top-Level Domains") at the top of the hierarchy.  [Root DNS zones/TLDs](https://www.iana.org/domains/root/db) are extremely numerous but some of the most commonly known zones include .com, .net, .org, .edu, .info, .tech, country codes, etc.  [Reserved root zones/TLDs](https://en.wikipedia.org/wiki/Special-use_domain_name) also exist that can only be used in private/non-public zones which are .example (including example.com, example.net, example.org), .invalid, .intranet, .internal, home, lan, .localhost, and .test.

Each root zone/TLD is divided into domains, with each level of the hierarchy separated by a dot, for example: **`www.example.com`**
		- .com is the root zone/TLD
		- example.com is the domain
		- www is a host or host record in the example.com domain

Domain names are managed by [Domain Name Registrars](https://en.wikipedia.org/wiki/Domain_name_registrar), which are responsible for assigning and tracking domain name reservations and IP addresses to organizations and individuals.  Domain name reservations can be searched, and additional reservation info queried, at the [ICANN DNS Database](https://www.icann.org/search) search page.

Domain zones are hosted by [Name Server(s)](https://en.wikipedia.org/wiki/Name_server).  Each domain has at least one [authoritative name server](https://en.wikipedia.org/wiki/Name_server#Authoritative_name_server) that publishes information about that domain and the name servers of any domains subordinate to it.[^1]  The Domain Name Server can also be configured to provide intended domain records to be available to the public internet space.  Another function of Name Servers is [reverse-lookups](https://en.wikipedia.org/wiki/Reverse_DNS_lookup), or DNS rewrites, to provide local network (LAN) address for [fully qualified domain names (FQDNs)](https://en.wikipedia.org/wiki/Fully_qualified_domain_name) whether publicly available or private only.

DNS also supports advanced features such as [DNSSEC](dns-dnssec.md) (DNS Security Extensions), which provides authentication and integrity checking for DNS queries and responses.

## DNS Record Types

DNS records are an essential part of the DNS system, as they contain the information needed to translate domain names into IP addresses and vice versa. Each DNS record contains a specific type of information about a domain name, such as its IP address, mail exchange server, or authoritative name servers.

There are many different types of DNS records, each with a specific format and purpose.  Common record types include, but are not limited to:

| Type  | Description |
|-------|-------------|
| A     | Translate domain name to an IP address.  One of the most basic and commonly used record types, but can only store IPv4 addresses.        |
| AAAA  | Functions similar to an "A" record but stores IPv6 addresses.         |
| CNAME | "Canonical name"; used instead of an "A" record as an alias to another domain.        |
| MX    | "Mail exchange"; stores instructions for directing email to mail servers.        |
| NS    | "Name server" record directs a DNS zone to use a specified authoritative name server.        |

Other commonly used DNS record include PTR, SOA, SRV, and TXT records. Each record type has a specific format and purpose, and is used to provide different types of information about a domain name.

Here's a [[dns-record-types|List of all DNS Record Types]].
## Popular third-party DNS hosts

1) [Cloudflare](https://www.cloudflare.com/) - Enterprise CDN with large catalog of available services.  Free account tier available.  Price for domain names is _at cost_ (they don't charge more for a domain name than the cost to them from the registrar).  DDoS protection, zero-trust tunnel, and secure outbound DNS resolution (DoH & DoT; see below) available at no additional cost.
2) [Ionos](https://www.ionos.com/) - Free domain for one year with a paid [hosting plan](https://www.ionos.com/hosting/web-hosting).  2gb email account included with registration.
3) [Namecheap](https://www.namecheap.com/) - Free authoritative name service if you already have a registered domain name.  Diverse spectrum of [subscription plans](https://www.namecheap.com/promos/) for specific service needs.
4) [GoDaddy](https://www.godaddy.com/) - World's largest domain registrar.  Free domain with annual plans.  Free email hosting with domain.  Comprehensive website builder for web hosting.
5) [A2Hosting](https://www.a2hosting.com/) - Basic paid web subscription plan includes 1 website and 100gb storage.  Basic paid email subscription includes 10gb storage.  Website builders of various application platforms available for additional cost.


>[!caution] 
>Hey: Ever wonder how those skeezy Internet Service Providers (ISPs) are able to compile and sell your internet browsing history if so many websites today are "secure" with HTTPS/TLS?  It's because your DNS queries are unencrypted and can be intercepted, read, and stored by anybody within your web path!!  Read on...
## Encryption

Ever since DNS was created in 1987, it has been largely unencrypted. Everyone between your device and the resolver is able to snoop on or even modify your DNS queries and responses.

The UDP source port is 53 which is the standard port number for unencrypted **DNS**. The [UDP](../networking/udp.md) payload is therefore likely to be a **DNS** answer.

Encrypting DNS makes it much harder for snoopers to look into your **DNS** messages, or to corrupt them in transit.

Two standardized mechanisms exist to secure the **DNS** transport between you and the resolver, [DNS over TLS](dns-dot.md), and [DNS queries over HTTPS](dns-doh.md).

Both are based on Transport Layer Security ([TLS](../networking/tls.md)) which is also used to secure communication between you and a website using [HTTPS](../networking/https.md).

As both DoT and DoH are relatively new, they are not universally deployed yet.  Continue in the subsections below for more about [[cheatsheets/networking/dns/dns-doh|DoH]] and [[cheatsheets/networking/dns/dns-dot|DoT]]!


---
[^1]: Source: [Wikipedia](https://en.wikipedia.org/wiki/Domain_Name_System)