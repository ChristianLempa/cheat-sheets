# Kubernetes "kubectl" Cheat-Sheet
## Config and Cluster Management
COMMAND | DESCRIPTION
---|---
`kubectl cluster-info` | Display endpoint information about the master and services in the cluster
`kubectl config view` |Get the configuration of the cluster
## Resource Management
COMMAND | DESCRIPTION
---|---
`kubectl get all --all-namespaces` | List all resources in the entire Cluster


### List of kubectl Short Names
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
## Logs and Troubleshooting
### Logs

### Executing Commands on Pods

### Networking
`kubectl run tmp-shell --rm -i --tty --image nicolaka/netshoot -- /bin/bash` 
### MySQL 
`kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -u USERNAME -h HOSTNAME -p`
