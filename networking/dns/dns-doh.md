# DNS over HTTPS (DoH)

**DNS over HTTPS** (**DoH**) is a protocol for performing remote Domain Name System (DNS) resolution via the [HTTPS](https://en.wikipedia.org/wiki/HTTPS_Proxy "HTTPS Proxy") protocol. A goal of the method is to increase user privacy and security by preventing eavesdropping and manipulation of DNS data by [man-in-the-middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attacks "Man-in-the-middle attacks")[[1]] by using the HTTPS protocol to [encrypt](https://en.wikipedia.org/wiki/Encrypt "Encrypt") the data between the DoH client and the DoH-based [DNS resolver](https://en.wikipedia.org/wiki/DNS_resolver "DNS resolver").[^1]

### Communication Protocol

With DNS over HTTPS (DoH) DNS queries and responses are encrypted, but they are sent via the HTTP or HTTP/2 protocols instead of unencrypted readable packets over UDP.  Like DoT, DoH ensures that attackers can't forge or alter DNS traffic.  DoH traffic over HTTPS or HTTP/2 are practically indiscernible from typical internet browsing.

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


---
[^1]: Source: [Wikipedia](https://en.wikipedia.org/wiki/DNS_over_HTTPS)