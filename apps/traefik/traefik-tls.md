# Traefik TLS Options and Settings

### ServersTransport

#### InsecureSkipVerify

If you want to skip the TLS verification from **Traefik** to your **Servers**, you can add the following section to your Traefik configuration file.

```yaml
serversTransport:
  insecureSkipVerify: true
```

### TLS Settings

Define TLS Settings in Traefik.

#### Default Certficicate

```yaml
tls:
  stores:
    default:
      defaultCertificate:
        certFile: /your-traefik-cert.crt
        keyFile: /your-traefik-key.key
```

#### TLS Options

Define TLS Options like disabling insecure TLS1.0 and TLS 1.1.

```yaml
tls:
  options:
    default:
      minVersion: VersionTLS12
```
