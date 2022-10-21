# K3S
Lightweight [Kubernetes](kubernetes.md). Production ready, easy to install, half the memory, all in a binary less than 100 MB.

Project Homepage: [K3s.io](https://www.k3s.io/)
Documentation: [K3s Documentation](https://docs.k3s.io/)

---
## Installation
To install k3s, you can follow different approaches.

**[K3s with external DB](k3s-install-ha-externaldb.md)** - Set up an HA K3s cluster backed by an external datastore such as MySQL, PostgreSQL, or etcd.

**[K3s with embedded DB](k3s-install-ha-embeddeddb.md)** - Set up an HA K3s cluster that leverages a built-in distributed database.

**[K3s single node](k3s-install-single.md)** -Set up K3s as a single node installation.

---
## Manage K3S
### Management on Server Nodes
`k3s kubectl`

### Download Kube Config
`/etc/rancher/k3s/k3s.yaml`


## Database Backups

### etcd snapshots
Stored in `/var/lib/rancher/k3s/server/db/snapshots`.

## Install a Cluster

```
curl https://get.k3s.io | INSTALL_K3S_VERSION="v1.18.13+k3s1" INSTALL_K3S_EXEC="server --write-kubeconfig-mode 0644 --tls-san foo.bar" sh -s -
```
