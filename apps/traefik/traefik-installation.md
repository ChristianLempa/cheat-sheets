# Traefik Installation Guideline

## Installation

### Docker

TODO: WIP

### Kubernetes

You can install **Traefik** via [Helm](../../kubernetes/helm.md).

```sh
helm repo add traefik https://traefik.github.io/charts

helm repo update

helm install traefik traefik/traefik
```
