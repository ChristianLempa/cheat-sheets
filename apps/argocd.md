# Argo CD
**Argo CD** is a declarative, GitOps continuous delivery tool for **Kubernetes ([[kubernetes]])**. It allows application definitions, configurations, and environments should be declarative and version controlled. Application deployment and lifecycle management should be automated, auditable, and easy to understand.

Documentation & Project Homepage: [Argo CD Docs](https://argo-cd.readthedocs.io/en/stable/)

---
## Installation

1. Install Argo CD on a **Kubernetes ([[kubernetes]])** Cluster, using **kubectl ([[kubectl]])**.

```bash
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

2. Add **Traefik IngressRoute ([[traefik]])**. 

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: argocd-server
  namespace: argocd
spec:
  entryPoints:
    - websecure
  routes:
    - kind: Rule
      match: Host(`argocd.example.com`)
      priority: 10
      services:
        - name: argocd-server
          port: 80
    - kind: Rule
      match: Host(`argocd.example.com`) && Headers(`Content-Type`, `application/grpc`)
      priority: 11
      services:
        - name: argocd-server
          port: 80
          scheme: h2c
  tls:
    certResolver: default
```

3. Disable internal TLS

Edit the `--insecure` flag in the `argocd-server` command of the argocd-server deployment, or simply set `server.insecure: "true"` in the `argocd-cmd-params-cm` ConfigMap.

---
## Get the admin password

For Argo CD v1.8 and earlier, the initial password is set to the name of the server pod, for Argo CD v1.9 and later, the initial password is available from a secret named `argocd-initial-admin-secret`.

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

---
## Configuration

### Add private GitHub Repositories

1. Create a github token: https://github.com/settings/tokens

2. Add new repository in ArgoCD via **kubectl ([[kubectl]])** or the GUI

```yaml
apiVersion: v1  
kind: Secret  
metadata:  
  name: repo-private-1
  labels:  
    argocd.argoproj.io/secret-type: repository  
stringData:  
  url: https://github.com/xcad2k/private-repo 
  password: <github-token> 
  username: not-used
```

3. Verify new repository is connected

---
