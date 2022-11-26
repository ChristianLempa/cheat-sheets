# Cert-Manager
Cert-manager adds certificates and certificate issuers as resource types in **Kubernetes ([[kubernetes]])** clusters, and simplifies the process of obtaining, renewing and using those certificates.

Documentation & Project Homepage: [Cert-Manager Docs](https://cert-manager.io/docs/)

---
## Self-Signed Certificates

### Upload existing CA.key and CA.crt files (Option 1)

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

### Create CA through Cert-manager (Option 2)

Create a new ClusterIssuer or Issuer object by using the selfSigned Attribute.

```yaml
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: root-issuer
spec:
  selfSigned: {}
```

--- 
## Troubleshooting

### Common Errors

**DNS Record not yet propagated**
The error, `Waiting for DNS-01 challenge propagation: DNS record for "your-dns-record" not yet propagated.`, might occur in the `challenge` object. Cert-Manager creates a TXT Record on the DNS provider and checks, whether the record is existing, before issuing the certificate. In a split-dns environment, this could be a problem when internal DNS Servers can't resolve the TXT Record on the Cloud DNS. You can use the `extraArgs` `--dns01-recursive-nameservers-only`, and `--dns01-recursive-nameservers=8.8.8.8:53,1.1.1.1:53`, to specific the DNS Resolvers used for the challenge.

**No solver found**
The error, `Failed to determine a valid solver configuration for the set of domains on the Order: no configured challenge solvers can be used for this challenge` might occur in the `order` object, when no solver can't be found for the DNS Hostname. Make sure your solvers have a corrent `dnsZones` configured that matches the DNS Hostnames Zone.

