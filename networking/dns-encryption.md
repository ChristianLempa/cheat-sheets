# DNS Encryption

Ever since [DNS](dns.md) was created in 1987, it has been largely unencrypted. Everyone between your device and the resolver is able to snoop on or even modify your DNS queries and responses.

The [UDP](udp.md) source port is 53 which is the standard port number for unencrypted DNS. The UDP payload is therefore likely to be a DNS answer.

Encrypting DNS makes it much harder for snoopers to look into your DNS messages, or to corrupt them in transit.

Two standardized mechanisms exist to secure the DNS transport between you and the resolver, [DNS over TLS](dns-over-tls.md), and [DNS queries over HTTPS](dns-over-https.md).

Both are based on [Transport Layer Security](tls.md) which is also used to secure communication between you and a website using HTTPS.

As both DoT and DoH are relatively new, they are not universally deployed yet.

## Legacy DNS (unencrypted)

```
  ┌─────────────────┐
  │   DNS Protocol  │
  ├─────────────────┤
  │   UDP Protocol  │
  │   (Port 53)     │
  ├─────────────────┤
  │   IP Protocol   │
  └─────────────────┘
```

## DNS over TLS

[DNS over TLS](dns-over-tls.md), or DoT, is a standard for encrypting DNS queries to keep them secure and private. DoT uses the same security protocol, TLS, that HTTPS websites use to encrypt and authenticate communications. (TLS is also known as "SSL.") DoT adds TLS encryption on top of the user datagram protocol (UDP), which is used for DNS queries.

```
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

## DNS over HTTPs

[DNS over HTTPS](dns-over-https.md), or DoH, is an alternative to DoT. With DoH, DNS queries and responses are encrypted, but they are sent via the HTTP or HTTP/2 protocols instead of directly over UDP. 

Like DoT, DoH ensures that attackers can't forge or alter DNS traffic. DoH traffic looks like other HTTPS traffic – e.g. normal user-driven interactions with websites and web apps – from a network administrator's perspective.

```
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
