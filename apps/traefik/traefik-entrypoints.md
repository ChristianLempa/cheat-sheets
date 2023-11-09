# Traefik EntryPoints

In **Traefik**, **entrypoints** are the network ports through which incoming traffic enters the proxy server. They define how traffic is received and processed.

Entry points primarily serve as endpoints for routing rules, allowing you to direct incoming requests to different services based on host, path, and other criteria. For example, you can configure Traefik to route traffic received on the entry point http with Host header example.com to a specific backend service.

Here's an example of defining entry points in a Traefik configuration file using YAML syntax.

```yaml
entryPoints:
  web:
    address: :80
  websecure:
    address: :443
```

## HTTP Redirection

HTTP redirection is a feature of entry points that allows you to automatically redirect traffic from one entry point to another. It is commonly used to redirect HTTP traffic to HTTPS for secure communication.

> :information_source: HTTP redirection from HTTP to HTTPS is recommended to enhance security, protect data integrity, ensure compliance, build trust with users, and potentially improve search engine rankings.

To enable HTTP redirection, add the following section to your Traefik configuration file.

```yaml
entryPoints:
  web:
    address: :80
    http:
      redirections:
        entryPoint:
          to: websecure
          scheme: https
```

> :warning: It's important to note that to enable HTTPS (SSL/TLS) support, you'll need to configure TLS certificates for the appropriate entry point as well.

## Custom EntryPoints

To add a custom entry point in Traefik, you need to modify the Traefik configuration file with the desired settings. Here's how you can add a custom entry point:

```yaml
entryPoints:
  custom:
    address: ":8080"
```
