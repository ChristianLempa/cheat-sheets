# Longhorn

Longhorn is a lightweight, reliable and easy-to-use distributed block storage system for [Kubernetes](kubernetes/kubernetes.md).

Project Homepage: [Longhorn Homepage](https://longhorn.io)
Documentation: [Longhorn Docs](https://longhorn.io/docs/)

---
## Installation

You can install Longhorn via [Helm](tools/helm.md). To customize values, follow the [Chart Default Values](https://github.com/longhorn/longhorn/blob/master/chart/values.yaml)

```shell
helm repo add longhorn https://charts.longhorn.io

helm repo update

helm install longhorn longhorn/longhorn
```

---
