# Kind

Using the Kind project, you are able to easily deploy a Kubernetes cluster on top of Docker as Docker containers. Kind will spawn separate containers which be shown as the Kubernetes nodes. In this documentation, you can find some examples, as well as a link to a Ansible playbook which can do the cluster creation / deletion for you. This document only describes the basics of Kind. To find more detailed information, you can check the [official Kind documentation](https://kind.sigs.k8s.io/docs/user/quick-start/).

Kind is ideal to use in a local development environment or even during a build pipeline run.

## Installation on Linux

Since Kind deploys Docker containers, it needs to have a Container engine (like Docker) installed.

Installing Kind can be done by downloading the latest available release / binary for your platform:

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.16.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

## Cluster management

### Cluster creation

You have to provide a configuration file which tells Kind how you want your Kubernetes cluster to be deployed. Find an example configuration file below:

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
name: testcluster
# 1 control plane node and 2 workers
nodes:
# the control plane node config
- role: control-plane
# the two workers
- role: worker
- role: worker
```

Create the cluster by the following command:

```bash
kind create cluster --config kind-cluster-config.yaml
Creating cluster "testcluster" ...
Ensuring node image (kindest/node:v1.25.2)
Preparing nodes
Writing configuration
Starting control-plane
Installing CNI
Installing StorageClass
Joining worker nodes

Set kubectl context to "kind-testcluster"
You can now use your cluster with:
kubectl cluster-info --context kind-testcluster

Not sure what to do next? Check out https://kind.sigs.k8s.io/docs/user/quick-start/
```

Checking for Docker containers running, you can see the following:

```bash
docker ps -a

CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
ac14d8c7a3c9 kindest/node:v1.25.2 "/usr/local/bin/entr..." 2 minutes ago Up About a minute testcluster-worker2
096dd4bf1718 kindest/node:v1.25.2 "/usr/local/bin/entr..." 2 minutes ago Up About a minute 127.0.0.1:42319->6443/tcp testcluster-control-plane
e1ae2d701394 kindest/node:v1.25.2 "/usr/local/bin/entr..." 2 minutes ago Up About a minute testcluster-worker
```

### Interacting with your cluster

You may have multiple Kind clusters deployed at the same time. To get a list of running clusters, you can use the following command:

```bash
kind get clusters
kind
kind-2
```

After cluster creation, the Kubernetes context is set automatically to the newly created cluster. In order to set the currently used kubeconfig, you may use some tooling like [kubectx](https://github.com/ahmetb/kubectx). You may also set the current context used by `kubectl` with the `--context` option, which refers to the Kind cluster name.

### Cluster deletion

To delete a Kind cluster, you can use the following command. Kind will also delete the kubeconfig of the deleted cluster. So you don't need to do this on your own.

```bash
kind delete cluster -n testcluster
Deleting cluster "testcluster" ...
```

## Further information

More examples and tutorials regarding Proxmox can be found in the link list below:

- Creating an Ansible playbook to manage Kind cluster: [Lightweight Kubernetes cluster using Kind and Ansible](https://thedatabaseme.de/2022/04/22/lightweight-kubernetes-cluster-using-kind-and-ansible/)
