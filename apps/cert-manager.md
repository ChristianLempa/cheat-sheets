# Cert-Manager
Cert-manager adds certificates and certificate issuers as resource types in **Kubernetes ([[kubernetes]])** clusters, and simplifies the process of obtaining, renewing and using those certificates.

Documentation & Project Homepage: [Cert-Manager Docs](https://cert-manager.io/docs/)

---
## Self-Signed Certificates

1. Create a self-signed CA ([[ssl-certs]]) creating a ca.key (private-key) and ca.crt (certificate)

(ca.key)
```bash
openssl genrsa -out ca.key 4096
```

(ca.crt)
```bash
openssl req -new -x509 -sha256 -days 365 -key ca.key -out ca.crt
```

2. Convert the files to a one line base64 decoded string (only works on Linux base64 tool)

```bash
cat ca.key | base64 -w 0
```

3. Create a new ssl secret object using the strings

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: ssl-issuer-secret
  # (Optional) Metadata
  # ---
  # namespace: your-namespace
type: Opaque
data:
  tls.crt: <base64-decoded-string>
  tls.key: <base64-decoded-string>
```

4. Create a new ClusterIssuer or Issuer object by using the ssl secret

```yaml
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: selfsigned-issuer
  # (Optional) Metadata
  # ---
  # namespace: your-namespace
spec:
  ca:
    secretName: ssl-issuer-secret
```

