# Traefik Cheat-Sheet


## Provider Specific Configuration
### Docker

**traefik.enable**
If `exposedByDefault` is disabled, Traefik won't automatically expose any containers by default. Setting `traefik.enable: true`, will expose the Container.

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