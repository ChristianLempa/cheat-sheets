# Traefik Middlewares

**Traefik Middlewares** are powerful tools for request manipulation and response enhancements. They can be used to modify requests, apply security measures, manage access control, and perform redirections.

## Middleware Configuration

To use a middleware in Traefik, you first define it and then attach it to [Traefik Routers](traefik-routers.md). Middlewares can be defined in Traefik's dynamic configuration.

> ℹ For more information on configuring Traefik, refer to the [Traefik General Configuration Guidelines](traefik-configuration.md).

### AddPrefix

Adds a prefix to the URL path.

```yaml
http:
  middlewares:
    add-prefix:
      addPrefix:
        prefix: "/new-prefix"
```

### BasicAuth

Protects your services with Basic Authentication.

```yaml
http:
  middlewares:
    basic-auth:
      basicAuth:
        users:
          - "username:hashedpassword"
```

### RateLimit

Limits the rate of requests.

```yaml
http:
  middlewares:
    rate-limit:
      rateLimit:
        average: 100
        burst: 50
```

### RedirectScheme

Redirects HTTP to HTTPS.

```yaml
http:
  middlewares:
    https-redirect:
      redirectScheme:
        scheme: https
        permanent: true
```

### StripPrefix

Removes the specified prefix from the URL path.

```yaml
http:
  middlewares:
    strip-prefix:
      stripPrefix:
        prefixes:
          - "/old-prefix"
```

## Attach Middleware to a Router

### Option 1

To attach a middleware to a router, add the following section to your Traefik configuration file.

```yaml
http:
  routers:
    your-router:
      middlewares:
        - your-middleware
```

### Option 2

Or you can use the `middlewares` label on the container.

```yaml
labels:
  - "traefik.http.routers.your-router.middlewares=your-middleware"
```

## Attach Middlewares to an IngressRoute

To attach a middleware to an IngressRoute, add the following section to your IngressRoute.

```yaml
spec:
  routes:
    - match: Host(`yourdomain.com`)
      kind: Rule
      middlewares:
        - name: your-middleware
```
