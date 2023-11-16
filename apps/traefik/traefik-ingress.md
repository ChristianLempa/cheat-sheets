# Traefik Ingress

In Traefik Ingress can be configured by using the built-in `Ingress` resource of Kubernetes, or custom `IngressRoute` resources provided by Traefik. `IngressRoute` resources offer more flexibility and features than the standard `Ingress` resource, but might not be compatible with other Ingress controllers.

## Ingress

To create an Ingress, add the following section to your Traefik configuration file.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  namespace: your-namespace
  annotations:
    traefik.ingress.kubernetes.io/router.entrypoints: web
spec:
  rules:
    - host: "yourdomain.com"
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: your-service-name
                port:
                  number: 80

```

## IngressRoute

> ℹ IngressRoute is a custom resource provided by Traefik. It is not compatible with other Ingress controllers. You need to make sure Traefik CRDs are existing in your cluster.

To create an IngressRoute, add the following section to your Traefik configuration file.

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: example-ingressroute
  namespace: your-namespace
spec:
  entryPoints:
    - web
  routes:
    - match: Host(`yourdomain.com`)
      kind: Rule
      services:
        - name: your-service-name
          port: 80
```

### IngressRoute with TLS

You can also create an IngressRoute with TLS enabled. To do so, add the following section to your IngressRoute.

```yaml
spec:
  tls:
    secretName: your-tls-secret
    domains:
    - main: your-domain.com
      sans:
      - "*.your-domain.com"
```

### IngressRoute with Middlewares

You can also create an IngressRoute with Middlewares. To do so, add the following section to your IngressRoute.

```yaml
spec:
  routes:
    - match: Host(`yourdomain.com`)
      kind: Rule
      middlewares:
        - name: your-middleware
      services:
        - name: your-service-name
          port: 80
```
