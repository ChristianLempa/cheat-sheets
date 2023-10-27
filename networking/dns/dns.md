# DNS

DNS (Domain Name System) is a hierarchical distributed naming system used to translate human-readable domain names, such as `www.example.com`, into [[IP]] (Internet Protocol) addresses, such as 192.0.2.1, that computers use to identify each other on the Internet. DNS allows users to access websites and other Internet resources using easy-to-remember domain names instead of having to remember the numerical IP addresses that correspond to them.

## How DNS works

DNS operates using a client-server architecture. When a user types a domain name into their web browser, the browser sends a DNS query to a DNS resolver, which is typically provided by the user’s Internet Service Provider (ISP). The resolver then sends a series of recursive queries to other DNS servers, working its way up the DNS hierarchy until it receives a response containing the IP address associated with the requested domain name.

DNS is organized into a hierarchical structure of domains, with the root domain at the top of the hierarchy. Each domain is divided into subdomains, with each level of the hierarchy separated by a dot (e.g., example.com is a subdomain of the com top-level domain). Each domain is managed by a domain name registrar, which is responsible for assigning domain names and IP addresses to organizations and individuals. DNS also supports advanced features such as [DNSSEC](dns-dnssec.md) (DNS Security Extensions), which provides authentication and integrity checking for DNS queries and responses.

## DNS Record Types

DNS records are an essential part of the DNS system, as they contain the information needed to translate domain names into IP addresses and vice versa. Each DNS record contains a specific type of information about a domain name, such as its IP address, mail exchange server, or authoritative name servers.

There are many different types of DNS records, each with a specific format and purpose. Some of the most commonly used DNS record types include A, AAAA, CNAME, MX, NS, PTR, SOA, SRV, and TXT records. Each record type has a specific format and purpose, and is used to provide different types of information about a domain name.

Here's a [[dns-record-types|List of all DNS Record Types]].

## Encryption

Ever since DNS was created in 1987, it has been largely unencrypted. Everyone between your device and the resolver is able to snoop on or even modify your DNS queries and responses.

The UDP source port is 53 which is the standard port number for unencrypted **DNS**. The [UDP](../networking/udp.md) payload is therefore likely to be a **DNS** answer.

Encrypting DNS makes it much harder for snoopers to look into your **DNS** messages, or to corrupt them in transit.

Two standardized mechanisms exist to secure the **DNS** transport between you and the resolver, [DNS over TLS](dns-dot.md), and [DNS queries over HTTPS](dns-doh.md).

Both are based on Transport Layer Security ([TLS](../networking/tls.md)) which is also used to secure communication between you and a website using [HTTPS](../networking/https.md).

As both DoT and DoH are relatively new, they are not universally deployed yet.

### DNS over HTTPS

DNS over HTTPS, or DoH, is an alternative to DoT. With DoH, DNS queries and responses are encrypted, but they are sent via the HTTP or HTTP/2 protocols instead of directly over UDP.

Like DoT, DoH ensures that attackers can't forge or alter DNS traffic. DoH traffic looks like other HTTPS traffic – e.g. normal user-driven interactions with websites and web apps – from a network administrator's perspective.

```txt
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

  GET/POST
  url/dns-request?dns-...
```

### DNS over TLS

DNS over TLS, or DoT, is a standard for encrypting DNS queries to keep them secure and private. DoT uses the same security protocol, TLS, that HTTPS websites use to encrypt and authenticate communications. (TLS is also known as "SSL.") DoT adds TLS encryption on top of the user datagram protocol (UDP), which is used for DNS queries.

```txt
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
```
