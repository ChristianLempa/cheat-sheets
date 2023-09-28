# Traefik Routers

### Configuring Routers

In Traefik, routers are a fundamental component responsible for routing incoming requests to the appropriate services based on specific conditions. Routers work together with entry points and middlewares to define how traffic is received and processed.

A router in Traefik is defined by various criteria such as the entry point, host, path, headers, and more. It acts as a rule-based engine, evaluating the incoming requests against those defined criteria and forwarding them to the appropriate backend services or middleware chains.

**traefik.http.routers.router.entrypoints**
Specifies the Entrypoint for the Router. Setting this to `traefik.http.routers.router.entrypoints: websecure` will expose the Container on the `websecure` entrypoint.
*When using websecure, you should enable `traefik.http.routers.router.tls` as well.

**traefik.http.routers.router.rule**
Specify the Rules for the Router.
*This is an example for an FQDN: Host(`subdomain.your-domain`)*

**traefik.http.routers.router.tls**	
Will enable TLS protocol on the router.

**traefik.http.routers.router.tls.certresolver**
Specifies the Certificate Resolver on the Router.

#### PathPrefix and StripPrefix

WIP

```yml
- "traefik.enable=true"
- "traefik.http.routers.nginx-test.entrypoints=websecure"
- "traefik.http.routers.nginx-test.tls=true"
- "traefik.http.routers.nginx-test.rule=PathPrefix(`/nginx-test/`)"
- "traefik.http.routers.nginx-test.middlewares=nginx-test"
- "traefik.http.middlewares.nginx-test.stripprefix.
prefixes=/nginx-test"
```

Add `/api` prefix to any requets to `myapidomain.com`
Example:

- Request -> `myapidomain.com`
- Traefik translates this to `myapidomain.com/api` without requestee seeing it

```yml
- "traefik.enable=true"
- "traefik.http.routers.myapp-secure-api.tls=true"
- "traefik.http.routers.myapp-secure-api.rule=Host(`myapidomain.com`)"
- "traefik.http.routers.myapp-secure-api.middlewares=add-api"

# Middleware
- "traefik.http.middlewares.add-api.addPrefix.prefix=/api"
```