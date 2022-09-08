# Kubernetes DNS

## Custom DNS Settings

### Edit coredns config map

Add entry to the `Corefile: |` section of the `configmap/coredns` in section **kube-system**.

```yml
.:53 {
  # ...
}
import /etc/coredns/custom/*.server
```

### Add new config map

Example for local DNS server using the **clcreative.home** zone.

```yml
apiVersion: v1
kind: ConfigMap
metadata:
  name: coredns-custom
  namespace: kube-system
data:
  clcreative.server: |
    clcreative.home:53 {
      forward . 10.20.0.10
    }
```