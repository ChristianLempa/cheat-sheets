# SSL Certificates Cheat-Sheet
## Generate Self-Signed Certificates
1. Generate a private RSA key `openssl genrsa -aes256 -out ca-key.pem 4096`
2. Generate a public CA Cert `openssl req -new -x509 -days 365 -key ca-key.pem -sha256 -out ca.pem`
3. `openssl genrsa -out cert-key.pem 4096`
4. `openssl req -subj "/CN=yourcn" -sha256 -new -key cert-key.pem -out cert.csr`
5. `echo "subjectAltName=DNS:your-dns.record,IP:257.10.10.1" >> extfile.cnf`
6. (optional) `echo extendedKeyUsage = serverAuth >> extfile.cnf`
7.  `openssl x509 -req -days 365 -sha256 -in cert.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out cert.pem -extfile extfile.cnf`


## Renew CA Cert
1. `openssl x509 -x509toreq -in ca.pem -signkey ca-key.pem -out ca.csr`
2. `openssl x509 -req -days 365 -in ca.csr -signkey ca.key -out new-ca.pem`

## Renew Cert
1. `openssl req -subj "/CN=yourcn" -sha256 -new -key cert-key.pem -out cert.csr`
2. `openssl x509 -req -days 365 -sha256 -in cert.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out cert.pem < extfile.cnf`

## Verify Cert
`openssl verify -CAfile ca.pem -verbose cert.pem`