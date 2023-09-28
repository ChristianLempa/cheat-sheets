# Traefik Certificate Resolvers

### Configuring Certificate Resolvers

In Traefik, certificate resolvers are components that handle the acquisition and management of TLS (Transport Layer Security) certificates for secure communication over HTTPS. They are responsible for obtaining, renewing, and storing the necessary certificates required for TLS encryption.

```yaml
certificatesResolvers:
  yourresolver:
    acme:
      email: "your-mail-address"
      httpChallenge:
        entryPoint: web
```

#### dnsChallenge

DNS Providers such as `cloudflare`, `digitalocean`, `civo`, and more. To get a full list of supported providers, look up the [Traefik ACME Documentation](https://doc.traefik.io/traefik/https/acme/) .

```yaml
certificatesResolvers:
  yourresolver:
    acme:
      email: "your-mail-address"
      dnsChallenge:
        provider: your-dns-provider
        resolvers:
          - "your-dns-resolver-ip-addr:53"
```
