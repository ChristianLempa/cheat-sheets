# Traefik Configuration

In Traefik, there are two types of configurations: dynamic configuration and static configuration:

- Static Configuration
- Dynamic Configuration

## Static Configuration

Static configuration refers to the initial configuration that is defined and loaded when Traefik starts. It includes global settings, entry points, routers, middlewares, and other configurations that provide an initial setup for routing and processing incoming requests.

> ℹ Once Traefik is running, the static configuration remains in effect until the service is restarted or reloaded.

Static configuration settings are typically defined in a configuration file (e.g., `traefik.yaml/traefik.yml` or `traefik.toml`) located in `/etc/traefik/` or provided as command-line arguments during startup.

## Dynamic Configuration

Dynamic configuration allows you to adjust and update Traefik's configuration during runtime without restarting or interrupting the service. It enables you to make changes to routing rules, add/remove backend services, modify middlewares, or adjust other configuration aspects without any service downtime.

Dynamic configuration in Traefik is achieved through **providers**. **Providers** fetch the configuration details from external sources (e.g., container orchestrators, service discovery systems) and update Traefik's routing table accordingly.

Traefik supports different types of **providers** to adapt to various infrastructure environments and source systems. Here are some commonly used **providers** in Traefik:

- File Provider
- Docker Provider
- Kubernetes Provider

### File

The File provider allows you to define configuration details in static files in different formats like YAML, JSON, or TOML. These files can be monitored for changes, and Traefik can dynamically update its configuration based on the changes.

```yaml
providers:
  file:
```

### Docker Provider

The Docker provider dynamically discovers containerized services deployed within Docker containers. It automatically sets up routes and backend configurations based on Docker container metadata and labels. As containers are started, stopped, or their labels are modified, Traefik adapts its routing accordingly.

```yaml
providers:
  docker:
```

With `exposedByDefault: false`, Traefik won't automatically expose any containers by default. Setting `traefik.enable: true`, will expose the Container.

```yaml
providers:
  docker:
    exposedByDefault: false
```

### Kubernetes Provider

The Kubernetes provider integrates with Kubernetes clusters to automatically discover and configure services based on Kubernetes resources. It can create routes and backend configurations based on Kubernetes Ingress or custom resource definitions like Traefik IngressRouteCRDs. It ensures that Traefik stays in sync with the Kubernetes environment as services are added, modified, or removed.

```yaml
providers:
  kubernetesCRD:
```
