# SSL Certificates Cheat-Sheet
## Generate Self-Signed Certificates
1. Generate a private RSA key `openssl genrsa -aes256 -out ca-key.pem 4096`
2. Generate a public CA Cert `openssl req -new -x509 -days 365 -key ca-key.pem -sha256 -out ca.pem`
3. `openssl genrsa -out server-key.pem 4096`
4. `openssl req -subj "/CN=yourcn" -sha256 -new -key server-key.pem -out server.csr`
5. `echo subjectAltName = DNS:your-dns.record,IP:257.10.10.1 >> extfile.cnf`
6. `echo extendedKeyUsage = serverAuth >> extfile.cnf`
7.  `openssl x509 -req -days 365 -sha256 -in server.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out server-cert.pem extfile.cnf`