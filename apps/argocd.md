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

### Declarative Application and ApplicationSet

Apart from using the WebUI to add managed apps to ArgoCD, you can configure `Application`
and `ApplicationSet` resources. This enables you to define not only ArgoCD and your apps
as code, but also the definition which application you want to manage.
With apps defined as YAML via an `Application`, you can e.g. deploy the app within a CI/CD
pipeline that deploys your Argo instance.

There are two types of resources. `Application` and `ApplicationSet`. The main difference is,
that you can specify so called inline generators which allow you to template your Application
definition. If you manage multiple clusters with ArgoCD and you want to get an `Application`
deployed with cluster specific parameters you want to use an `ApplicationSet`.

Below, you find an example for an `Application` and an `ApplicationSet`.

**Application:**

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: guestbook
  namespace: argocd
spec:
  destination:
    namespace: default
    server: 'https://kubernetes.default.svc'
  source:
    path: kustomize-guestbook
    repoURL: 'https://github.com/argoproj/argocd-example-apps'
    targetRevision: HEAD
  project: default
  syncPolicy:
    automated:
      prune: false
      selfHeal: false
```

**ApplicationSet:**

```yaml
apiVersion: argoproj.io/v1alpha1
kind: ApplicationSet
metadata:
  name: guestbook
  namespace: argocd
spec:
  generators:
  - clusters: {} # This is a generator, specifically, a cluster generator.
  template: 
    # This is a template Argo CD Application, but with support for parameter substitution.
    metadata:
      name: '{{name}}-guestbook'
    spec:
      project: "default"
      source:
        repoURL: https://github.com/argoproj/argocd-example-apps/
        targetRevision: HEAD
        path: kustomize-guestbook
      destination:
        server: '{{server}}'
        namespace: default
```

## Further information

More examples and tutorials regarding ArgoCD can be found in the link list below:

- Basic tutorial for installation and configuration: [Let loose the squid - Deploy ArgoCD the declarative way](https://thedatabaseme.de/2022/06/05/let-loose-the-squid-deploy-argocd-the-declarative-way/)
- Writing ArgoCD Plugins: [ArgoCD Custom Plugins](https://dev.to/tylerauerbeck/argocd-custom-plugins-creating-a-custom-plugin-to-process-openshift-templates-4p5m)