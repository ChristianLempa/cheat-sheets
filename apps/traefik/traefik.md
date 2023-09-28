# Traefik

**Traefik** is a popular open-source reverse proxy and load balancer designed for modern microservices and containerized applications. It acts as a gateway between your infrastructure and the services running within it, providing dynamic routing, [SSL/TLS](../../networking/tls.md) termination, and automatic discovery of new services. **Traefik** supports popular container orchestration platforms like [Docker](../../docker/docker.md) and [Kubernetes](../../kubernetes/kubernetes.md) and can adapt to the changing infrastructure by automatically configuring itself based on the available services and their metadata.

## Installation

**Traefik** can be installed using [Docker](../../docker/docker.md) or in a [Kubernetes](../../kubernetes/kubernetes.md) cluster by using [Helm](../../kubernetes/helm.md).

For more information on installing **Traefik**, refer to the [Traefik Installation Guidelines](traefik-installation.md).

## Configuration

Traefik can be configured through a configuration file (YAML or TOML), command-line arguments, or environment variables, providing flexibility in defining settings for entry points, routers, services, and more based on your deployment environment and preferences.

For more information on configuring Traefik, refer to the [Traefik General Configuration Guidelines](traefik-configuration.md).

## Features

Traefik offers a range of features that make it a powerful and versatile reverse proxy and load balancer. Some notable features of Traefik, and how to configure them, are listed below:

- [EntryPoints](traefik-entrypoints.md)
- [Routers](traefik-routers.md)
- [Middlewares](traefik-middlewares.md)
- [Ingress](traefik-ingress.md)
- [Certificate Resolvers](traefik-certresolvers.md)
- [TLS Options and Settings](traefik-tls.md)
- [Logging and Troubleshooting](traefik-troubleshooting.md)

## References

- [Traefik Documentation](https://doc.traefik.io/traefik/)
- [Traefik GitHub](https://github.com/traefik/traefik)
- [Traefik Docker Hub](https://hub.docker.com/_/traefik)
