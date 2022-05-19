# Kubectl Cheat-Sheet
...

---
##  Install Kubectl
### On Windows (PowerShell)
Install Kubectl with **Chocolatey** ([[chocolatey]]):
```
choco install kubernetes-cli
```

### On Linux
> [!INFO] Installing on WSL2
> On WSL2 it's recommended to install Docker Desktop [[docker-desktop]], which automatically comes with kubectl.
1. Download the latest release
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"  
```

2. Install Kubectl
```bash
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

---
##  Config Management

...

### Multiple Config Files

...

**On Windows (PowerShell**
```powershell
$env:KUBECONFIG = "$HOME/.kube/prod-k8s-clcreative-kubeconfig.yaml;$HOME/.kube/infra-home-kube-prod-1.yml;$HOME/.kube/infra-home-kube-demo-1.yml;$HOME/.kube/infra-cloud-kube-prod-1.yml"
```

**On Linux**
```bash
export KUBECONFIG=~/.kube/kube-config-1.yml:~/.kube/ube-config-2.yml
```

---
##  Commands
### Networking
Connect containers using Kubernetes internal DNS system:
`<service-name>.<namespace>.svc.cluster.local`

Troubleshoot Networking with a netshoot toolkit Container:
`kubectl run tmp-shell --rm -i --tty --image nicolaka/netshoot -- /bin/bash`

### Containers
Restart Deployments (Stops and Restarts all Pods):
`kubectl scale deploy <deployment> --replicas=0`
`kubectl scale deploy <deployment> --replicas=1`

Executing Commands on Pods:
`kubectl exec -it <PODNAME> -- <COMMAND>`
`kubectl exec -it generic-pod -- /bin/bash` 

### Config and Cluster Management
COMMAND | DESCRIPTION
---|---
`kubectl cluster-info` | Display endpoint information about the master and services in the cluster
`kubectl config view` |Get the configuration of the cluster
### Resource Management
COMMAND | DESCRIPTION
---|---
`kubectl get all --all-namespaces` | List all resources in the entire Cluster
`kubectl delete <RESOURCE> <RESOURCENAME> --grace-period=0 --force` | Try to force the deletion of the resource

---
## ﴱ List of Kubernetes Resources "Short Names"

Short Name | Long Name
---|---
`csr`|`certificatesigningrequests`
`cs`|`componentstatuses`
`cm`|`configmaps`
`ds`|`daemonsets`
`deploy`|`deployments`
`ep`|`endpoints`
`ev`|`events`
`hpa`|`horizontalpodautoscalers`
`ing`|`ingresses`
`limits`|`limitranges`
`ns`|`namespaces`
`no`|`nodes`
`pvc`|`persistentvolumeclaims`
`pv`|`persistentvolumes`
`po`|`pods`
`pdb`|`poddisruptionbudgets`
`psp`|`podsecuritypolicies`
`rs`|`replicasets`
`rc`|`replicationcontrollers`
`quota`|`resourcequotas`
`sa`|`serviceaccounts`
`svc`|`services`

---
## 陼 Logs and Troubleshooting
...

### Logs
...

### MySQL 
`kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -u USERNAME -h HOSTNAME -p`

---
## Resources stuck in Terminating state
...

### Namespaces
1. Save the namespace in a `YOUR-NAMESPACE.json` file.
```
kubectl get ns YOUR-NAMESPACE -o json > YOUR-NAMESPACE.json
```

2. Edit the `YOUR-NAMESPACE.json` and remove the section in `Finalizers`.

3. Update the NAMESPACE.
```
kubectl replace --raw "/api/v1/namespaces/YOUR-NAMESPACE/finalize" -f .\YOUR-NAMESACE.json
```
