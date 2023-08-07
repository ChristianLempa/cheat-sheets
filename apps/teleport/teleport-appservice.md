# Teleport App Service

The [Teleport](teleport.md) App Service is a secure and convenient way to access internal applications from anywhere. It uses Teleport's built-in IAM system to authenticate users, and allows users to access applications from a web browser or command-line client. The Teleport App Service can be scaled to support numerous users and applications.

## Requirements

> To securely access applications, you need to obtain a valid [SSL/TLS certificate](../../misc/ssl-certs.md) for the Teleport, and its application subdomains.

### Example: wildcard certificate in [Traefik](../traefik/traefik.md)

```yaml
labels:
- "traefik.http.routers.teleport.rule=HostRegexp(`teleport.your-domain`, `{subhost:[a-z]+}.teleport.your-domain`)"
- "traefik.http.routers.teleport.tls.domains[0].main=teleport.your-domain"
- "traefik.http.routers.teleport.tls.domains[0].sans=*.teleport.your-domain"
```

## Configuration

The following snippet shows the full YAML configuration of an Application Service appearing in the `teleport.yaml` configuration file:

```yaml
app_service:
  enabled: yes
  apps:
  - name: "grafana"
    description: "This is an internal Grafana instance"
    uri: "http://localhost:3000"
    public_addr: "grafana.teleport.example.com".  # (optional)
    insecure_skip_verify: false  # (optional) don't very certificate
```

## Usage

To access a configured application in the Teleport UI, you can either:
- Go to the **Applications** tab and click the **Launch** button for the application that you want to access.
- Enter the subdomain of the application in your web browser, e.g. `https://grafana.teleport.example.com`.

### Relevant CLI commands

List the available applications:

```sh
tsh apps ls
```

Retrieves short-lived X.509 certificate for CLI application access.

```sh
tsh apps login grafana
```

