# Argo CD
**Argo CD** is a declarative, GitOps continuous delivery tool for **Kubernetes ([[kubernetes]])**. It allows application definitions, configurations, and environments should be declarative and version controlled. Application deployment and lifecycle management should be automated, auditable, and easy to understand.

Documentation & Project Homepage: [Argo CD Docs](https://argo-cd.readthedocs.io/en/stable/)

---
### Add private GitHub Repositories
1. Create a github token: https://github.com/settings/tokens
2. Add new repository in ArgoCD via **kubectl ([[kubectl]])** or the GUI
```
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