# tmp 

`kubectl run tmp-shell --rm -i --tty --image nicolaka/netshoot -- /bin/bash` container for troubleshooting

`kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -u USERNAME -h HOSTNAME -p`
container for mysql client

## List of kubectl Short Names
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
