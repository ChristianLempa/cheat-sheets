# Argo CD



### Add private GitHub Repositories
1. Create a github token: https://github.com/settings/tokens
2. Add new repository in ArgoCD via kubectl or the GUI
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