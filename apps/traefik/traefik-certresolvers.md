# Traefik Certificate Resolvers

Certificate Resolvers are used to obtain and renew certificates for TLS (Transport Layer Security) communication over HTTPS. Traefik supports two types of certificate resolvers: `httpChallenge`, `tlsChallenge` and `dnsChallenge`.

## HTTP Challenge

HTTP Challenge is the default challenge type. It is used to obtain certificates for domains that are publicly accessible. When using HTTP Challenge, Traefik must be reachable by Let's Encrypt through port 80.

```yaml
certificatesResolvers:
  yourresolver:
    acme:
      email: "your-mail-address"
      httpChallenge:
        entryPoint: web
```

## TLS Challenge

TLS Challenge is used to obtain certificates for domains that are not publicly accessible. When using TLS Challenge, Traefik must be reachable by Let's Encrypt through port 443.

```yaml
certificatesResolvers:
  yourresolver:
    acme:
      email: "your-mail-address"
      tlsChallenge: {}
```

## DNS Challenge

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

### Custom DNS Servers

By default, Traefik uses the DNS servers configured on the host, which can be problematic when using local DNS Servers for example. If you want to use custom DNS servers, you can specify them in the `resolvers` section of the DNS challenge.

```yaml
certificatesResolvers:
  yourresolver:
    acme:
      email: "your-mail-address"
      dnsChallenge:
        provider: your-dns-provider
        resolvers:
          - "1.1.1.1:53"
          - "8.8.8.8:53"
```

## Staging and Production

By default, Traefik uses the Let's Encrypt production environment `https://acme-v02.api.letsencrypt.org/directory`. For testing purposes, you should add the `caServer` option to your certificate resolver, and set it to `https://acme-staging-v02.api.letsencrypt.org/directory`. This has much higher rate limits than the production environment.

```yaml
certificatesResolvers:
  yourresolver:
    acme:
      email: "your-mail-address"
      caServer: "https://acme-staging-v02.api.letsencrypt.org/directory"
      httpChallenge:
        entryPoint: web
```
