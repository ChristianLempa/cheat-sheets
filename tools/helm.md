---
tags:
    - kubernetes
categories:
    - kubernetes
---

# Helm Cheat-Sheet

***Helm*** is a package manager for [Kubernetes](kubernetes.md).

The ***tiller*** component runs on your Kubernetes cluster, listens for commands from helm, and handles the configuration and deployment of software releases on the cluster.

## Installation

* [macOS](../macos/macos.md): `brew install helm`
* Windows: `choco install kubernetes-helm`
* [Ubuntu](../linux/linux.md):
    * `sudo snap install helm --classic`
    * `curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -`
    * `sudo apt-get install apt-transport-https --yes`
    * `echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list`
    * `sudo apt-get update`
    * `sudo apt-get install helm`
* [RedHat/CentOs/Amazon Linux](../linux/linux.md)
    * `curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 > get_helm.sh`
    * `chmod 700 get_helm.sh`
    * `./get_helm.sh`
    * ***helm*** installed in `/usr/local/bin/helm`


## Example commands

* <code>helm (command)</code>
* <code>helm --help</code>
* <code>helm search --help</code>
* <code>helm install</code>
* <code>helm status</code>
* <code>helm create mychart</code>
* <code>helm list</code>
* <code>helm repo list</code>
* <code>helm repo add eks https://aws.github.io/eks-charts</code>
* <code>helm repo add stable https://kubernetes-charts.storage.googleapis.com/</code>
* <code>helm repo update</code>
* <code>helm search repo stable</code>
* <code>helm get manifest</code>
* <code>helm upgrade</code>

Software available: Artifactory, datadog, Elastic, fluentd, GitLab, graylog, MySQL

## Repository Management
COMMAND | DESCRIPTION
---|---
`helm repo list` | List Helm repositories
`helm repo update` | Update list of Helm charts from repositories

## Chart Management
COMMAND | DESCRIPTION
---|---
`helm search` | List all installed charts
`helm search <CHARTNAME>` | Search for a chart
`helm ls` | List all installed Helm charts
`helm ls --deleted` | List all deleted Helm charts
`helm ls --all` | List installed and deleted Helm charts
`helm inspect values <REPO>/<CHART>` | Inspect the variables in a chart

## Install/Delete Helm Charts
COMMAND | DESCRIPTION
---|---
`helm install --name <NAME> <REPO>/<CHART>` | Install a Helm chart
`helm install --name <NAME> --values <VALUES.YML> <REPO>/<CHART>` | Install a Helm chart and override variables
`helm status <NAME>` | Show status of Helm chart being installed
`helm delete --purge <NAME>` | Delete a Helm chart

## Upgrading Helm Charts
COMMAND | DESCRIPTION
---|---
`helm get values <NAME>` | Return the variables for a release
`helm upgrade --values <VALUES.YML> <NAME> <REPO>/<CHART>` | Upgrade the chart or variables in a release
`helm history <NAME>` | List release numbers
`helm rollback <NAME> 1` | Rollback to a previous release number

## Creating Helm Charts
COMMAND | DESCRIPTION
---|---
`helm create <NAME>` | Create a blank chart
`helm lint <NAME>` | Lint the chart
`helm package <NAME>` | Package the chart into foo.tgz
`helm dependency update` | Install chart dependencies

## Chart Folder Structure
```
wordpress/
  Chart.yaml          # A YAML file containing information about the chart
  LICENSE             # OPTIONAL: A plain text file containing the license for the chart
  README.md           # OPTIONAL: A human-readable README file
  requirements.yaml   # OPTIONAL: A YAML file listing dependencies for the chart
  values.yaml         # The default configuration values for this chart
  charts/             # A directory containing any charts upon which this chart depends.
  templates/          # A directory of templates that, when combined with values,
                      # will generate valid Kubernetes manifest files.
  templates/NOTES.txt # OPTIONAL: A plain text file containing short usage notes
```

## See also

- [kubernetes](kubernetes.md)
- [docker](../docker/docker.md)
