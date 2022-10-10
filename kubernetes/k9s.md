# K9s
K9s is a command line interface to easy up managing Kubernetes([[kubernetes]]) clusters.

Core features of k9s are for instance:
- Editing of resource manifests
- Shell into a Pod / Container
- Manage multiple Kubernetes clusters using one tool

More information and current releases of k9s, can be found on their [Github repository](https://github.com/derailed/k9s).

**Screenshots:**

<img src="https://github.com/derailed/k9s/blob/master/assets/screen_po.png?raw=true"/>
<img src="https://github.com/derailed/k9s/blob/master/assets/screen_logs.png?raw=true"/>
<img src="https://github.com/derailed/k9s/blob/master/assets/screen_dp.png?raw=true"/>

---
## Installation

### On Linux

1. Find and download the latest release

Check the release page [here](https://github.com/derailed/k9s/releases) and search for the
fitting package type (e.g. Linux_x86_64). Copy the link to the archive of your choice.
Download and unpack the archive like in this example:

```bash
wget https://github.com/derailed/k9s/releases/download/v0.26.6/k9s_Linux_x86_64.tar.gz
tar -xvf k9s_Linux_x86.tar.gz
```

2. Install k9s
```bash
sudo install -o root -g root -m 0755 k9s /usr/local/bin/k9s
```

---
## Commands

### Cluster selection
As soon as you've started k9s, you can use a bunch of commands to interact with your selected
cluster (which is the context you have selected in you current shell environment).

You can everytime change the cluster you want to work with by typing `:context`. A list of
available cluster configurations appear, you can select the cluster to connect to with the
arrow keys and select the context to be used by pressing enter.

### General command structure

**Menu**
You can switch between resource types to show using a text menu selection. You need to press `:`
to bring up this menu. Then you can type the resource type you want to switch to
(e.g. `pod`, `services`...). Press the enter key to finish the command. 

**Selection**
Selections are made with the arrow keys. To confirm your selection or to show more information,
use the enter key again. For instance, you can select a pod with the arrow keys and type enter
to "drill down" in that pod and view the running containers in it.

**Filter and searches**
In nearly every screen of k9s, you can apply filters or search for something (e.g. in the log output
of a pod). This can be done by pressing `/` followed by the search / filter term. Press enter so apply
the filter / search.
Also in some screens, there are shortcuts for namespace filters bound to the number keys. Where `0`
always shows all namespaces.

### Useful shortcuts and commands

| Command     | Comment                                                                        | Compareable kubectl command                                               |
|-------------|--------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| `:pod`      | Switches to the pod screen, where you can see all pods on the current cluster. | `kubectl get pods --all-namespaces`                                       |
| `:services` | Switches to the service screen, where you can see all services.                | `kubectl get services --all-namespaces`                                   |
| `ctrl`+`d`  | Delete a resource.                                                             | `kubectl delete <resource> -n <namespace>`                                |
| `ctrl`+`k`  | Kill a resource (no confirmation)                                              |                                                                           |
| `s`         | When on the Pod screen, you then open a shell into the selected pod.           | `kubectl exec -n <namespace> <pod_name> -c <container_name> -- /bin/bash` |
| `l`         | Show the log output of a pod.                                                  | `kubectl logs -n <namespace> <pod_name>`                                  |