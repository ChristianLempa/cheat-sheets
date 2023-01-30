# TLS

Transport Layer Security (TLS) is a cryptographic protocol designed to provide communications security over a [computer network](network.md). The protocol is widely used in applications such as email, instant messaging, and voice over IP, but its use in securing HTTPS remains the most publicly visible.

The TLS protocol aims primarily to provide security, including privacy (confidentiality), integrity, and authenticity through the use of cryptography, such as the use of certificates, between two or more communicating computer applications. It runs in the application layer and is itself composed of two layers: the TLS record and the TLS handshake protocols.

TLS is a proposed Internet Engineering Task Force (IETF) standard, first defined in 1999, and the current version is TLS 1.3, defined in August 2018. TLS builds on the now-deprecated SSL (Secure Sockets Layer) specifications (1994, 1995, 1996) developed by Netscape Communications for adding the HTTPS protocol to their Navigator web browser.

## TLS Handshake

In a TLS/SSL handshake, clients and servers exchange SSL certificates, cipher suite requirements, and randomly generated data for creating session keys.

TLS handshakes are a foundational part of how HTTPS works.

SSL, or Secure Sockets Layer, was the original encryption protocol developed for HTTP. SSL was replaced by TLS, or Transport Layer Security, some time ago. SSL handshakes are now called TLS handshakes, although the "SSL" name is still in wide use.

<pre>
┌──────────┐                 ┌──────────┐
│  Client  │                 │  Server  │
└─────┬────┘                 └─────┬────┘
      │                            │
      │                            │ 
      │ ─────────────────────────► │  ──┐
      │ 1. SYN                     │    │
      │                            │    │
      │                            │    │ TCP
      │ ◄───────────────────────── │    │
      │ 3. ACK          2. SYN ACK │  ──┘
      │                            │
      │ -------------------------- │
      │                            │
      │ ─────────────────────────► │  ──┐
      │ 4. ClientHello             │    │
      │                            │    │
      │ ◄───────────────────────── │    │
      │             5. ServerHello │    │
      │                Certificate │    │
      │            ServerHelloDone │    │
      │                            │    │ TLS
      │ ─────────────────────────► │    │
      │ 6. ClientKeyExchange       │    │
      │    ChangeCipherSpec        │    │
      │    Finished                │    │
      │                            │    │
      │ ◄───────────────────────── │    │
      │        7. ChangeCipherSpec │    │
      │           Finished         │  ──┘
        --------------------------
</pre>
