# Install K3S in High Availability Mode
## Install Database
Install [MariaDB](../databases/mariadb.md).
## Install Servers
```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--datastore-endpoint='mysql://user:pass@tcp(ipaddress:3306)/dbname' \
--node-taint CriticalAddonsOnly=true:NoExecute \
--tls-san your-dns-name --tls-san your-lb-ip-address
```
### Node-Taint
By default, server nodes will be schedulable and thus your workloads can get launched on them. If you wish to have a dedicated control plane where no user workloads will run, you can use taints. The node-taint parameter will allow you to configure nodes with taints, for example `--node-taint CriticalAddonsOnly=true:NoExecute`.

### SSL Certificates
To avoid certificate errors in such a configuration, you should install the server with the `--tls-san YOUR_IP_OR_HOSTNAME_HERE` option. This option adds an additional hostname or IP as a Subject Alternative Name in the TLS cert, and it can be specified multiple times if you would like to access via both the IP and the hostname.

## Get a registered Address

## Install Agents
  
```bash
curl -sfL https://get.k3s.io | sh -s - agent \
--server https://your-lb-ip-address:6443 \
--token YOUR-SECRET
```
