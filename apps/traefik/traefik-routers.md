# Traefik Routers

Traefik routers are responsible for connecting incoming requests to the services that should handle them. They determine how requests are routed to these services based on rules defined in the configuration.

## Router Configuration

### Option 1

Routers can be defined as part of Traefik's dynamic configuration.

```yaml
http:
  routers:
    my-router:
      rule: "Host(`example.com`) && Path(`/mypath`)"
      service: my-service
      # Additional configurations can be added here
```

> ℹ For more information on configuring Traefik, refer to the [Traefik General Configuration Guidelines](traefik-configuration.md).

### Option 2

Or you can configure the `routers` label in the container definition.

```yaml
- "traefik.enable=true"
- "traefik.http.routers.my-router.rule=Host(`example.com`) && Path(`/mypath`)"
- "traefik.http.routers.my-router.service=my-service"
```

## Router Options

### Specifying Entry Points

Define which entry points (like HTTP or HTTPS) the router should listen to:

```yaml
services:
  my-service:
    labels:
      - "traefik.http.routers.my-router.entrypoints=websecure"
```

### HTTPS and TLS Configuration

To enable TLS for the router:

```yaml
services:
  my-service:
    labels:
      - "traefik.http.routers.my-secure-router.rule=Host(`example.com`)"
      - "traefik.http.routers.my-secure-router.service=my-service"
      - "traefik.http.routers.my-secure-router.tls=true"
```

To enable TLS with a custom certificate resolver:

```yaml
services:
  my-service:
    labels:
      - "traefik.http.routers.my-secure-router.rule=Host(`example.com`)"
      - "traefik.http.routers.my-secure-router.service=my-service"
      - "traefik.http.routers.my-secure-router.tls=true"
      - "traefik.http.routers.my-secure-router.tls.certresolver=myresolver"
```

> ℹ For more information on configuring TLS, refer to the [Traefik TLS Configuration Guidelines](traefik-tls.md).

### Middlewares

To attach a middleware to a router:

```yaml
services:
  my-service:
    labels:
      - "traefik.http.routers.my-router.middlewares=my-middleware"
```

> ℹ For more information on configuring middlewares, refer to the [Traefik Middlewares Guidelines](traefik-middlewares.md).

### Load Balancing

Load balancers allow you to configure the applications internal service ports and load balancing strategy.

```yaml
services:
  my-service:
    labels:
      - "traefik.http.routers.my-router.rule=Host(`example.com`)"
      - "traefik.http.routers.my-router.service=my-service"
      - "traefik.http.services.my-service.loadbalancer.server.port=80"
      - "traefik.http.services.my-service.loadbalancer.sticky=true"
```

Other load balancing strategies include sticky sessions, round-robin, and more.
