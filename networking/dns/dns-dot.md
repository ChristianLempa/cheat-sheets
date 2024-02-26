# DNS over TLS (DoT)

**DNS over TLS** (**DoT**) is a network [security protocol](https://en.wikipedia.org/wiki/Security_protocol "Security protocol") for encrypting and wrapping [Domain Name System](https://en.wikipedia.org/wiki/Domain_Name_System "Domain Name System") (DNS) queries and answers via the [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (TLS) protocol. The goal of the method is to increase user privacy and security by preventing eavesdropping and manipulation of DNS data via [man-in-the-middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attacks "Man-in-the-middle attacks"). The [well-known port number](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers "List of TCP and UDP port numbers") for DoT is 853.[^1]

## Communication Protocol

DoT uses the same security protocol, TLS, that HTTPS websites use to encrypt and authenticate communications. (TLS is also known as "SSL.") DoT adds TLS encryption on top of the user datagram protocol (UDP), which is used for DNS queries.

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


---
[^1]: Source: [Wikipedia](https://en.wikipedia.org/wiki/DNS_over_HTTPS)