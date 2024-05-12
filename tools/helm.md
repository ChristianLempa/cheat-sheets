# Helm

## Repository Management

| Command | Description |
| --- | --- |
| `helm repo list` | List Helm repositories |
| `helm repo update` | Update list of Helm charts from repositories |

## Chart Management

| Command | Description |
| --- | --- |
| `helm search` | List all installed charts |
| `helm search <chart>` | Search for a chart |
| `helm ls` | List all installed Helm charts |
| `helm ls --deleted` | List all deleted Helm charts |
| `helm ls --all` | List installed and deleted Helm charts |
| `helm inspect values <repo>/<chart>` | Inspect the variables in a chart |

## Install/Delete Helm Charts

| Command | Description |
| --- | --- |
| `helm install --name <name> <repo>/<chart>` | Install a Helm chart |
| `helm install --name <name> --values <VALUES.YML> <repo>/<chart>` | Install a Helm chart and override variables |
| `helm status <name>` | Show status of Helm chart being installed |
| `helm delete --purge <name>` | Delete a Helm chart |

## Upgrading Helm Charts

| Command | Description |
| --- | --- |
| `helm get values <name>` | Return the variables for a release |
| `helm upgrade --values <file> <name> <repo>/<chart>` | Upgrade the chart or variables in a release |
| `helm history <name>` | List release numbers |
| `helm rollback <name> 1` | Rollback to a previous release number |

## Creating Helm Charts

| Command | Description |
| --- | --- |
| `helm create <name>` | Create a blank chart |
| `helm lint <name>` | Lint the chart |
| `helm package <name>` | Package the chart into foo.tgz |
| `helm dependency update` | Install chart dependencies |
