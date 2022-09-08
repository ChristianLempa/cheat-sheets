# Install K3S in High Availability Mode with an embedded Database
## Install first Server
```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--tls-san your-dns-name --tls-san your-lb-ip-address \
--cluster-init
```

### SSL Certificates
To avoid certificate errors in such a configuration, you should install the server with the `--tls-san YOUR_IP_OR_HOSTNAME_HERE` option. This option adds an additional hostname or IP as a Subject Alternative Name in the TLS cert, and it can be specified multiple times if you would like to access via both the IP and the hostname.

## Install additional Servers
```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--tls-san your-dns-name --tls-san your-lb-ip-address \
--server https://IP-OF-THE-FIRST-SERVER:6443
```

## ETCD Fault Tolerance
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

## Get a registered Address
To achieve a high-available scenario you also need to load balance incoming connections between the server nodes.
### Sophos XG NAT Rule
You can do this by creating a Load-Balance NAT Rule on the Sophos XG Firewall.
1. Create a new `IP Host` object from type `IP List`.
2. Add all IP addresses from the Server nodes
3. Add an additional IP Address to your incoming interface
4. Create a new NAT Rule to MASQ (SNAT) the incoming traffic on the additional IP Address to the `IP Host` object. Once you do this you can specify the Load-Balancing Method in the Advanced Settings
5. Set a Load Balancing Method like Round-robing f.e. and enable Health Checks to failover in case of a node outage

## Install Agents
You can still add additional nodes without a server function to this cluster.
```bash
curl -sfL https://get.k3s.io | sh -s - agent \
--server https://your-lb-ip-address:6443 \
--token YOUR-SECRET
```
