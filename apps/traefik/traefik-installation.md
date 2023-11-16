# Traefik Installation Guideline

Traefik can be installed using Docker or in a Kubernetes cluster.

> ⚠ This installation method is a quick way to get started with Traefik. For more advanced use cases such as Docker and Kubernetes, check out my [Boilerplates Repository](https://github.com/christianlempa/boilerplates).

## Docker

Create a `docker-compose.yml` File:

```yaml
services:
  traefik:
    image: traefik:latest
    command:
      - "--api.insecure=true"
      - "--api.dashboard=true"
      - "--providers.docker=true"
      - "--providers.docker.exposedbydefault=false"
    ports:
      - "80:80"
      - "443:443"
      - "8080:8080"
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
```

Start Traefik:

```sh
Run docker-compose up -d to start Traefik.
```

Alternatively, you can run Traefik directly using the Docker CLI, to get quickly up and running.

```sh
docker run -d -p 80:80 -p 443:443 -p 8080:8080 --name traefik \
    -v /var/run/docker.sock:/var/run/docker.sock \
    traefik:latest --api.insecure=true --api.dashboard=true --providers.docker=true --providers.docker.exposedbydefault=false
```

## Kubernetes

To install **Traefik** via [Helm](../../kubernetes/helm.md), add the official Traefik Helm chart repository, and install the chart:

```sh
helm repo add traefik https://traefik.github.io/charts

helm repo update

helm install traefik traefik/traefik
```
