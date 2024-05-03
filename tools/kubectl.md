# Kubectl Cheat-Sheet

## Contexts and Configuration

| Command | Description |
| --- | --- |
| `kubectl config view` | Show the current kubeconfig file |
| `kubectl config get-contexts` | List all contexts in the kubeconfig file |
| `kubectl config current-context` | Show the current context |
| `kubectl config use-context <CONTEXT>` | Change the current context |
| `kubectl config set-context <CONTEXT> --namespace=<NAMESPACE>` | Set the namespace for a context |
| `kubectl config set-context <CONTEXT> --cluster=<CLUSTER>` | Set the cluster for a context |
| `kubectl config set-context <CONTEXT> --user=<USER>` | Set the user for a context |
| `kubectl config set-context <CONTEXT> --namespace=<NAMESPACE> --cluster=<CLUSTER> --user=<USER>` | Set all context properties |

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
| `kubectl apply -f <FILE>` | Apply a configuration file |
| `kubectl delete -f <FILE>` | Delete a configuration file |
| `kubectl get <RESOURCE>` | List all resources of a type |
| `kubectl describe <RESOURCE> <NAME>` | Describe a resource |
| `kubectl edit <RESOURCE> <NAME>` | Edit a resource |
| `kubectl exec -it <POD> -- <COMMAND>` | Execute a command in a pod |

## Pod Management

| Command | Description |
| --- | --- |
| `kubectl run <NAME> --image=<IMAGE>` | Create a new pod |
| `kubectl delete pod <NAME>` | Delete a pod |
| `kubectl get pod <NAME>` | Get details of a pod |
| `kubectl describe pod <NAME>` | Describe a pod |
| `kubectl logs <NAME>` | Show logs of a pod |
| `kubectl exec -it <NAME> -- /bin/bash` | Execute a command in a pod |
| `kubectl cp <POD>:<SRC> <DEST>` | Copy files from a pod |
| `kubectl top node` | Show metrics for all nodes |
| `kubectl top pod` | Show metrics for all pods |
| `kubectl top pod <NAME>` | Show metrics for a specific pod |

## Service Management

| Command | Description |
| --- | --- |
| `kubectl expose pod <NAME> --port=444 --target-port=555` | Expose a pod as a service |
| `kubectl delete service <NAME>` | Delete a service |
| `kubectl get service <NAME>` | Get details of a service |
| `kubectl describe service <NAME>` | Describe a service |

## Deployment Management

| Command | Description |
| --- | --- |
| `kubectl create deployment <NAME> --image=<IMAGE>` | Create a new deployment |
| `kubectl delete deployment <NAME>` | Delete a deployment |
| `kubectl get deployment <NAME>` | Get details of a deployment |
| `kubectl describe deployment <NAME>` | Describe a deployment |
| `kubectl scale deployment <NAME> --replicas=3` | Scale a deployment to 3 replicas |
| `kubectl rollout status deployment/<NAME>` | Check the status of a deployment rollout |
| `kubectl rollout history deployment/<NAME>` | Show the history of a deployment rollout |
| `kubectl rollout undo deployment/<NAME>` | Rollback a deployment to the previous version |
| `kubectl rollout undo deployment/<NAME> --to-revision=1` | Rollback a deployment to a specific revision |

## Namespace Management

| Command | Description |
| --- | --- |
| `kubectl create namespace <NAME>` | Create a new namespace |
| `kubectl delete namespace <NAME>` | Delete a namespace |
| `kubectl get namespace <NAME>` | Get details of a namespace |
| `kubectl describe namespace <NAME>` | Describe a namespace |
