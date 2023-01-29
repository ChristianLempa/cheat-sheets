# TLS

## TLS Handshake

In a TLS/SSL handshake, clients and servers exchange SSL certificates, cipher suite requirements, and randomly generated data for creating session keys.

TLS handshakes are a foundational part of how HTTPS works.

SSL, or Secure Sockets Layer, was the original encryption protocol developed for HTTP. SSL was replaced by TLS, or Transport Layer Security, some time ago. SSL handshakes are now called TLS handshakes, although the "SSL" name is still in wide use.

```
┌───────────┐                ┌───────────┐
│  Client  │                │  Server  │
└─────┬─────┘                └─────┬─────┘
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

```