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
| `helm search <CHARTNAME>` | Search for a chart |
| `helm ls` | List all installed Helm charts |
| `helm ls --deleted` | List all deleted Helm charts |
| `helm ls --all` | List installed and deleted Helm charts |
| `helm inspect values <REPO>/<CHART>` | Inspect the variables in a chart |

## Install/Delete Helm Charts

| Command | Description |
| --- | --- |
| `helm install --name <NAME> <REPO>/<CHART>` | Install a Helm chart |
| `helm install --name <NAME> --values <VALUES.YML> <REPO>/<CHART>` | Install a Helm chart and override variables |
| `helm status <NAME>` | Show status of Helm chart being installed |
| `helm delete --purge <NAME>` | Delete a Helm chart |

## Upgrading Helm Charts

| Command | Description |
| --- | --- |
| `helm get values <NAME>` | Return the variables for a release |
| `helm upgrade --values <VALUES.YML> <NAME> <REPO>/<CHART>` | Upgrade the chart or variables in a release |
| `helm history <NAME>` | List release numbers |
| `helm rollback <NAME> 1` | Rollback to a previous release number |

## Creating Helm Charts

| Command | Description |
| --- | --- |
| `helm create <NAME>` | Create a blank chart |
| `helm lint <NAME>` | Lint the chart |
| `helm package <NAME>` | Package the chart into foo.tgz |
| `helm dependency update` | Install chart dependencies |
