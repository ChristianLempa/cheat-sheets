# DNS

## DNS Cheat Sheets

- [BIND](bind.md)
- [Dig utility](../security/dig.md)
- [DNS encryption](dns-encryption.md)
- [DNS over https](dns-over-https.md)
- [DNS over tls](dns-over-tls.md)
- [DNS record mailserver](dns-record-mailserver.md)
- [DNS record types](dns-record-types.md)

## Overview

The Domain Name System (DNS) is a hierarchical and distributed naming system for computers, services, and other resources in the Internet or other Internet Protocol (IP) networks. It associates various information with domain names assigned to each of the associated entities. Most prominently, it translates readily memorized domain names to the numerical IP addresses needed for locating and identifying computer services and devices with the underlying network protocols. The Domain Name System has been an essential component of the functionality of the Internet since 1985.

The Domain Name System delegates the responsibility of assigning domain names and mapping those names to Internet resources by designating authoritative name servers for each domain. Network administrators may delegate authority over sub-domains of their allocated name space to other name servers. This mechanism provides distributed and fault-tolerant service and was designed to avoid a single large central database.

The Domain Name System also specifies the technical functionality of the database service that is at its core. It defines the DNS protocol, a detailed specification of the data structures and data communication exchanges used in the DNS, as part of the Internet Protocol Suite.

The Internet maintains two principal namespaces, the domain name hierarchy and the Internet Protocol (IP) address spaces. The Domain Name System maintains the domain name hierarchy and provides translation services between it and the address spaces. Internet name servers and a communication protocol implement the Domain Name System. A DNS name server is a server that stores the DNS records for a domain; a DNS name server responds with answers to queries against its database.

The most common types of records stored in the DNS database are for Start of Authority (SOA), IP addresses (A and AAAA), SMTP mail exchangers (MX), name servers (NS), pointers for reverse DNS lookups (PTR), and domain name aliases (CNAME). Although not intended to be a general purpose database, DNS has been expanded over time to store records for other types of data for either automatic lookups, such as DNSSEC records, or for human queries such as responsible person (RP) records. As a general purpose database, the DNS has also been used in combating unsolicited email (spam) by storing a real-time blackhole list (RBL). The DNS database is traditionally stored in a structured text file, the zone file, but other database systems are common.

The Domain Name System originally used the [User Datagram Protocol (UDP)](udp.md) as transport over IP. Reliability, security, and privacy concerns spawned the use of the [Transmission Control Protocol (TCP)](tcp.md) as well as numerous other protocol developments.

## DNS Encryption

Ever since DNS was created in 1987, it has been largely unencrypted. Everyone between your device and the resolver is able to snoop on or even modify your DNS queries and responses.

The UDP source port is 53 which is the standard port number for unencrypted DNS. The UDP payload is therefore likely to be a DNS answer.

Encrypting DNS makes it much harder for snoopers to look into your DNS messages, or to corrupt them in transit.

Two standardized mechanisms exist to secure the DNS transport between you and the resolver, [DNS over TLS](dns-over-tls.md), and [DNS queries over HTTPS](dns-over-https.md).

Both are based on Transport Layer Security ([TLS](tls.md)) which is also used to secure communication between you and a website using [HTTPS](https.md).

As both DoT and DoH are relatively new, they are not universally deployed yet.

### DNS over HTTPS

DNS over HTTPS, or DoH, is an alternative to DoT. With DoH, DNS queries and responses are encrypted, but they are sent via the HTTP or HTTP/2 protocols instead of directly over UDP. 

Like DoT, DoH ensures that attackers can't forge or alter DNS traffic. DoH traffic looks like other HTTPS traffic – e.g. normal user-driven interactions with websites and web apps – from a network administrator's perspective.

<pre>
  ┌─────────────────┐ ──┐
  │ 爵 HTTP Protocol │   │  encrypted
  ├─────────────────┤   ├── traffic
  │  TLS Protocol  │   │   via HTTPS
  ├─────────────────┤ ──┘
  │   TCP Protocol  │
  │   (Port 443)    │
  ├─────────────────┤
  │   IP Protocol   │
  └─────────────────┘
</pre>
```
  GET/POST
  url/dns-request?dns-...
```

### DNS over TLS

DNS over TLS, or DoT, is a standard for encrypting DNS queries to keep them secure and private. DoT uses the same security protocol, TLS, that HTTPS websites use to encrypt and authenticate communications. (TLS is also known as "SSL.") DoT adds TLS encryption on top of the user datagram protocol (UDP), which is used for DNS queries.

<pre>
  ┌─────────────────┐ ──┐
  │   DNS Protocol  │   │  encrypted
  ├─────────────────┤   ├── traffic
  │  TLS Protocol  │   │   via TLS
  ├─────────────────┤ ──┘
  │   UDP Protocol  │
  │   (Port 853)    │
  ├─────────────────┤
  │   IP Protocol   │
  └─────────────────┘
</pre>
