# SSL Certificates Cheat-Sheet

## Self-Signed Certificates

### Generate CA
1. Generate RSA`openssl genrsa -aes256 -out ca-key.pem 4096`
2. Generate a public CA Cert `openssl req -new -x509 -days 365 -key ca-key.pem -sha256 -out ca.pem`

### Generate Certificate
1. `openssl genrsa -out cert-key.pem 4096`
2. `openssl req -subj "/CN=yourcn" -sha256 -new -key cert-key.pem -out cert.csr`
3. `echo "subjectAltName=DNS:your-dns.record,IP:257.10.10.1" >> extfile.cnf`
4. (optional) `echo extendedKeyUsage = serverAuth >> extfile.cnf`
5.  `openssl x509 -req -days 365 -sha256 -in cert.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out cert.pem -extfile extfile.cnf`

### Renew Cert
1. `openssl req -subj "/CN=yourcn" -sha256 -new -key cert-key.pem -out cert.csr`
2. `openssl x509 -req -days 365 -sha256 -in cert.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out cert.pem < extfile.cnf`

## Verify Certificates
`openssl verify -CAfile ca.pem -verbose cert.pem`

## Install CA Cert in trusted root CAs

### on Linux

1. Move the `ca.pem` into `/usr/local/share/ca-certificates/ca.crt`.
2. Update the Cert Store `update-ca-certificates`

### on Windows

TODO: ...

### On Android

TODO: ...