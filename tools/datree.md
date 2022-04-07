# Datree
Datree can be used on the command line to run policies against Kubernetes manifests YAML files or Helm charts.

## Manifests
### Installation
**Windows** (PowerShell)
```powershell
iwr -useb https://get.datree.io/windows_install.ps1 | iex

setx PATH "$env:path;C:\Users\$env:UserName\AppData\Local\datree" -m
```

**Linux** (Bash)
```bash
sudo apt -y install unzip

curl https://get.datree.io | /bin/bash
```

### Usage
```bash
datree test ~/.datree/k8s-demo.yaml
```

## Helm
A Helm plugin to validate charts against the Datree policy.

>Only works on Linux

### Installation
```bash
helm plugin install https://github.com/datreeio/helm-datree
```

### Usage
Trigger datree policy check via the helm CLI
```bash
helm datree test [CHART_DIRECTORY]
```

If you need to pass helm arguments to your template, you will need to add -- before them:
```bash
helm datree test [CHART_DIRECTORY] -- --values values.yaml --set name=prod
```
