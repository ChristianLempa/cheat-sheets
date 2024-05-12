# Kubectl Cheat-Sheet

## Contexts and Configuration

| Command | Description |
| --- | --- |
| `kubectl config view` | Show the current kubeconfig file |
| `kubectl config get-contexts` | List all contexts in the kubeconfig file |
| `kubectl config current-context` | Show the current context |
| `kubectl config use-context <context>` | Change the current context |
| `kubectl config set-context <context> --namespace=<namespace>` | Set the namespace for a context |
| `kubectl config set-context <context> --cluster=<cluster>` | Set the cluster for a context |
| `kubectl config set-context <context> --user=<user>` | Set the user for a context |
| `kubectl config set-context <context> --namespace=<namespace> --cluster=<cluster> --user=<user>` | Set all context properties |

## Cluster Management

| Command | Description |
| --- | --- |
| `kubectl cluster-info` | Display addresses of the master and services |
| `kubectl get nodes` | List all nodes in the cluster |
| `kubectl get pods` | List all pods in the cluster |
| `kubectl get services` | List all services in the cluster |
| `kubectl get deployments` | List all deployments in the cluster |
| `kubectl get namespaces` | List all namespaces in the cluster |
| `kubectl get events` | List all events in the cluster |

## Resource Management

| Command | Description |
| --- | --- |
| `kubectl apply -f <file>` | Apply a configuration file |
| `kubectl delete -f <file>` | Delete a configuration file |
| `kubectl get <resource>` | List all resources of a type |
| `kubectl describe <resource> <name>` | Describe a resource |
| `kubectl edit <resource> <name>` | Edit a resource |
| `kubectl exec -it <pod> -- <command>` | Execute a command in a pod |

## Pod Management

| Command | Description |
| --- | --- |
| `kubectl run <name> --image=<image>` | Create a new pod |
| `kubectl delete pod <name>` | Delete a pod |
| `kubectl get pod <name>` | Get details of a pod |
| `kubectl describe pod <name>` | Describe a pod |
| `kubectl logs <name>` | Show logs of a pod |
| `kubectl exec -it <name> -- /bin/bash` | Execute a command in a pod |
| `kubectl cp <pod>:<source> <destination>` | Copy files from a pod |
| `kubectl top node` | Show metrics for all nodes |
| `kubectl top pod` | Show metrics for all pods |
| `kubectl top pod <name>` | Show metrics for a specific pod |

## Service Management

| Command | Description |
| --- | --- |
| `kubectl expose pod <name> --port=444 --target-port=555` | Expose a pod as a service |
| `kubectl delete service <name>` | Delete a service |
| `kubectl get service <name>` | Get details of a service |
| `kubectl describe service <name>` | Describe a service |

## Deployment Management

| Command | Description |
| --- | --- |
| `kubectl create deployment <name> --image=<image>` | Create a new deployment |
| `kubectl delete deployment <name>` | Delete a deployment |
| `kubectl get deployment <name>` | Get details of a deployment |
| `kubectl describe deployment <name>` | Describe a deployment |
| `kubectl scale deployment <name> --replicas=3` | Scale a deployment to 3 replicas |
| `kubectl rollout status deployment/<name>` | Check the status of a deployment rollout |
| `kubectl rollout history deployment/<name>` | Show the history of a deployment rollout |
| `kubectl rollout undo deployment/<name>` | Rollback a deployment to the previous version |
| `kubectl rollout undo deployment/<name> --to-revision=1` | Rollback a deployment to a specific revision |

## Namespace Management

| Command | Description |
| --- | --- |
| `kubectl create namespace <name>` | Create a new namespace |
| `kubectl delete namespace <name>` | Delete a namespace |
| `kubectl get namespace <name>` | Get details of a namespace |
| `kubectl describe namespace <name>` | Describe a namespace |
