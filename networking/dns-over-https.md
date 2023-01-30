# DNS over HTTPS

DNS over HTTPS (DoH) is a protocol for performing remote Domain Name System ([DNS](dns.md)) resolution via the HTTPS protocol. A goal of the method is to increase user privacy and security by preventing eavesdropping and manipulation of DNS data by man-in-the-middle attacks by using the HTTPS protocol to encrypt the data between the DoH client and the DoH-based DNS resolver. By March 2018, Google and the Mozilla Foundation had started testing versions of DNS over HTTPS. In February 2020, Firefox switched to DNS over HTTPS by default for users in the United States.

An alternative to DoH is the [DNS over TLS](dns-over-tls.md) (DoT) protocol, a similar standard for encrypting DNS queries, differing only in the methods used for encryption and delivery. Based on privacy and security, whether which protocol is superior is a matter of controversial debate; while others argue the merits of either depend on the specific use case.

## Deployment scenarios

DoH is used for recursive DNS resolution by DNS resolvers. Resolvers (DoH clients) must have access to a DoH server hosting a query endpoint.

Three usage scenarios are common:

- Using a DoH implementation within an application: Some browsers have a built-in DoH implementation and can thus perform queries by bypassing the operating system's DNS functionality. A drawback is that an application may not inform the user if it skips DoH querying, either by misconfiguration or lack of support for DoH.
- Installing a DoH proxy on the name server in the local network: In this scenario client systems continue to use traditional (port 53 or 853) DNS to query the name server in the local network, which will then gather the necessary replies via DoH by reaching DoH-servers in the Internet. This method is transparent to the end user.
- Installing a DoH proxy on a local system: In this scenario, operating systems are configured to query a locally running DoH proxy. In contrast to the previously mentioned method, the proxy needs to be installed on each system wishing to use DoH, which might require a lot of effort in larger environments.
