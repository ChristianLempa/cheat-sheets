# Datree
Datree can be used on the command line to run policies against Kubernetes manifests YAML files or Helm charts. It prevents Kubernetes misconfigurations from reaching production.

As your organization's infrastructure owner, the product’s stability is your primary concern. Toolchain engineering and architecture gets pushed to the wayside because you must constantly put out fires configured in the development stage.

## Installation

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

**Usage**
```bash
datree test ~/.datree/k8s-demo.yaml
```

## Policies
"Centralized policy" is the concept of controlling distributed policy execution from a centralized location. This concept enables the policy owner to easily control the rules that are evaluated in each run of Datree without creating operation overhead. The centralized policy can be managed by logging into the dashboard.

To run the Datree CLI against the new policy (instead of the default one), you will need to add the `-p POLICYNAME` to your policy check execution:

```
datree test ~/.datree/k8s-demo.yaml -p POLICYNAME
```


### Helm
A Helm plugin to validate charts against the Datree policy.
> [!attention]
> Only works on Linux


**Installation Linux** (Bash)
```bash
helm plugin install https://github.com/datreeio/helm-datree


### Usage
Trigger datree policy check via the helm CLI
```bash
helm datree test [CHART_DIRECTORY]
```


**Usage**

If you need to pass helm arguments to your template, you will need to add -- before them:

```bash
helm datree test [CHART_DIRECTORY] -- --values values.yaml --set name=prod
```
