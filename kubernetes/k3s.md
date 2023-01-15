# K3S
Lightweight [Kubernetes](kubernetes/kubernetes.md). Production ready, easy to install, half the memory, all in a binary less than 100 MB.

Project Homepage: [K3s.io](https://www.k3s.io/)
Documentation: [K3s Documentation](https://docs.k3s.io/)

---
## Installation

To install k3s, you can follow different approaches like setting up k3s with an **external database**, **embedded database**, or as a **single node**.


### K3s with external DB

Set up an HA K3s cluster backed by an external datastore such as MySQL, PostgreSQL, or etcd.

#### Install Database

Install [MariaDB](databases/mariadb.md).

#### Install Servers
```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--datastore-endpoint='mysql://user:pass@tcp(ipaddress:3306)/dbname' \
--node-taint CriticalAddonsOnly=true:NoExecute \
--tls-san your-dns-name --tls-san your-lb-ip-address
```

#### Node-Taint

By default, server nodes will be schedulable and thus your workloads can get launched on them. If you wish to have a dedicated control plane where no user workloads will run, you can use taints. The node-taint parameter will allow you to configure nodes with taints, for example `--node-taint CriticalAddonsOnly=true:NoExecute`.

#### SSL Certificates

To avoid certificate errors in such a configuration, you should install the server with the `--tls-san YOUR_IP_OR_HOSTNAME_HERE` option. This option adds an additional hostname or IP as a Subject Alternative Name in the TLS cert, and it can be specified multiple times if you would like to access via both the IP and the hostname.

#### Get a registered Address

TODO: WIP

#### Install Agents

TODO: WIP

```bash
curl -sfL https://get.k3s.io | sh -s - agent \
--server https://your-lb-ip-address:6443 \
--token YOUR-SECRET
```


### K3s with embedded DB

Set up an HA K3s cluster that leverages a built-in distributed database.

TODO: WIP

#### Install first Server

TODO: WIP

```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--tls-san your-dns-name --tls-san your-lb-ip-address \
--cluster-init
```

To avoid certificate errors in such a configuration, you should install the server with the `--tls-san YOUR_IP_OR_HOSTNAME_HERE` option. This option adds an additional hostname or IP as a Subject Alternative Name in the TLS cert, and it can be specified multiple times if you would like to access via both the IP and the hostname.

#### Install additional Servers

TODO: WIP

```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--tls-san your-dns-name --tls-san your-lb-ip-address \
--server https://IP-OF-THE-FIRST-SERVER:6443
```

The `--cluster-init` initializes an HA Cluster with an embedded etcd database. The fault tolerance requires an odd number, minimum three, nodes to function.

Total Number of nodes | Failed Node Tolerance
---|---
1|0
2|0
3|1
4|1
5|2
6|2
...|...

#### Get a registered Address

To achieve a high-available scenario you also need to load balance incoming connections between the server nodes.

TODO: WIP

#### Install Agents

You can still add additional nodes without a server function to this cluster.

```bash
curl -sfL https://get.k3s.io | sh -s - agent \
--server https://your-lb-ip-address:6443 \
--token YOUR-SECRET
```


### K3s single node

Set up K3s as a single node installation.

TODO: WIP

---
## Manage K3S
### Management on Server Nodes
`k3s kubectl`

### Download Kube Config
`/etc/rancher/k3s/k3s.yaml`


## Database Backups

### etcd snapshots
Stored in `/var/lib/rancher/k3s/server/db/snapshots`.
