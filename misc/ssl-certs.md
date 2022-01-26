# SSL Certificates Cheat-Sheet

X.509 is an ITU standard defining the format of public key certificates. X.509 are used in TLS/SSL, which is the basis for HTTPS. An X.509 certificate binds an identity to a public key using a digital signature. A certificate contains an identity (hostname, organization, etc.) and a public key (RSA, DSA, ECDSA, ed25519, etc.), and is either signed by a Certificate Authority or is Self-Signed.

## Self-Signed Certificates

### Generate CA
1. Generate RSA `openssl genrsa -aes256 -out ca-key.pem 4096`
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

## Certificate Formats

X.509 Certificates exist in Base64 Formats **PEM (.pem, .crt, .ca-bundle)**, **PKCS#7 (.p7b, p7s)** and Binary Formats **DER (.der, .cer)**, **PKCS#12 (.pfx, p12)**. 

### Convert Certs

COMMAND | CONVERSION
---|---
`openssl x509 -outform der -in cert.pem -out cert.der` | PEM to DER
`openssl x509 -inform der -in cert.der -out cert.pem` | DER to PEM
`openssl pkcs12 -in cert.pfx -out cert.pem -nodes` | PFX to PEM

## Verify Certificates
`openssl verify -CAfile ca.pem -verbose cert.pem`

## Install CA Cert in trusted root CAs

### On Linux

1. Move the `ca.pem` into `/usr/local/share/ca-certificates/ca.crt`.
2. Update the Cert Store `update-ca-certificates`

### On Windows

Assuming path to your generated CA certificate as `C:\ca.pem`, 

1. Use the `Import-Certificate` Powershell Cmdlet for this.
2. Run `Import-Certificate -FilePath "C:\ca.pem" -CertStoreLocation Cert:\LocalMachine\Root`.
  - Set `-CertStoreLocation` to `Cert:\CurrentUser\Root` in case you want to trust certificates only for the logged in user.

OR

- In Command Prompt, use `certutil.exe` for this.
- Run `certutil.exe -addstore root C:\ca.pem` for system-wide trust.

### On Android

The process varies device-to-device. But generally follows as:
1. Open Phone Settings
2. Locate `Encryption and Credentials` section.
  - Use the search box for it.
  - Generally it is found under `Settings > Security > Encryption and Credentials`
4. Choose `Install a certificate`
5. Choose `CA Certificate`
6. Locate the certificate file `ca.pem` on your SD Card/Internal Storage using the File Manager
7. Select it and DONE!
