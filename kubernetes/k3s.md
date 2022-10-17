# K3S
Lightweight [[kubernetes|Kubernetes]]. Production ready, easy to install, half the memory, all in a binary less than 100 MB.

Project Homepage: [K3s.io](https://www.k3s.io/)
Documentation: [K3s Documentation](https://docs.k3s.io/)

---
## Installation
To install k3s, you can follow different approaches.

**[[k3s-install-ha-externaldb|K3s with external DB]]** - Set up an HA K3s cluster backed by an external datastore such as MySQL, PostgreSQL, or etcd.

**[[k3s-install-ha-embeddeddb|K3s with embedded DB]]** - Set up an HA K3s cluster that leverages a built-in distributed database.

**[[k3s-install-single|K3s single node]]** -Set up K3s as a single node installation.

---
## Manage K3S
### Management on Server Nodes
`k3s kubectl`

### Download Kube Config
`/etc/rancher/k3s/k3s.yaml`


## Database Backups

### etcd snapshots
Stored in `/var/lib/rancher/k3s/server/db/snapshots`.
