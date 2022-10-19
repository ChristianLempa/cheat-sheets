# Rancher
**Rancher**, the open-source multi-cluster orchestration platform, lets operations teams deploy, manage and secure enterprise **[Kubernetes](../kubernetes/kubernetes.md)**.

Project Homepage: [Rancher Homepage](https://www.rancher.com)

---
## Remove Installation

```
kubectl delete validatingwebhookconfiguration rancher.cattle.io
kubectl delete mutatingwebhookconfiguration rancher.cattle.io
```

