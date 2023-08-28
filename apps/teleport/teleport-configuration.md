# Teleport Configuration

In order to avoid breaking existing configurations, Teleport's configuration is versioned. The newer configuration version is `v3`. If a `version` is not specified in the configuration file, `v1` is assumed.

## Instance-wide settings

### Log Settings

```yaml
teleport:
  log:
    output: stderr
    severity: INFO
    format:
      output: text
```

## Proxy Service

```yaml
proxy_service:
  enabled: "yes"
  web_listen_addr: 0.0.0.0:3080
  # -- (Optional) when using reverse proxy
  # public_addr: ['your-server-url:443']
  https_keypairs: []
  acme: {}
  # --(Optional) ACME
  # acme:
  #   enabled: "yes"
  #   email: your-email-address
```

## Auth Service

```yaml
auth_service:
  enabled: "yes"
  listen_addr: 0.0.0.0:3025
  proxy_listener_mode: multiplex
  cluster_name: your-server-url
```

## Additional Services Configuration

- [SSH Service](teleport-ssh)
- [Kubernetes Service](teleport-kubernetes)
- [Application Service](teleport-appservice)
- [Databases Service](teleport-databases)
- [Remote Desktop Service](teleport-remotedesktop)
