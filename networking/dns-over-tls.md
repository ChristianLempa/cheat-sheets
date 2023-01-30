# DNS over TLS

DNS over TLS (DoT) is a network security protocol for encrypting and wrapping Domain Name System (DNS) queries and answers via the Transport Layer Security (TLS) protocol. The goal of the method is to increase user privacy and security by preventing eavesdropping and manipulation of DNS data via man-in-the-middle attacks. The well-known port number for DoT is 853.

While DNS-over-TLS is applicable to any DNS transaction, it was first standardized for use between stub or forwarding resolvers and recursive resolvers, in RFC 7858 in May of 2016. Subsequent IETF efforts specify the use of DoT between recursive and authoritative servers ("Authoritative DNS-over-TLS" or "ADoT") and a related implementation between authoritative servers (Zone Transfer-over-TLS or "xfr-over-TLS").

[BIND](bind.md) supports DoT connections as of version 9.17.

## Alternatives

[DNS over HTTPS](dns-over-https.md) (DoH) is a similar protocol standard for encrypting DNS queries, differing only in the methods used for encryption and delivery from DoT. On the basis of privacy and security, whether or not a superior protocol exists among the two is a matter of controversial debate, while others argue the merits of either depend on the specific use case.

DNSCrypt is another network protocol that authenticates and encrypts DNS traffic, although it was never proposed to the Internet Engineering Task Force (IETF) with a Request for Comments (RFC).
