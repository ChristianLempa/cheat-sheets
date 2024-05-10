# OpenSSL Cheat-Sheet

## Certificate Management

| Command | Description |
| --- | --- |
| `openssl req -new -key KEYFILE -out CSRFILE` | Generate a new certificate signing request |
| `openssl req -x509 -key KEYFILE -in CSRFILE -out CERTFILE` | Generate a self-signed certificate |
| `openssl x509 -in CERTFILE -text -noout` | Display the details of a certificate |
| `openssl x509 -in CERTFILE -pubkey -noout` | Extract the public key from a certificate |
| `openssl x509 -in CERTFILE -fingerprint -noout` | Display the fingerprint of a certificate |

## Key Management

| Command | Description |
| --- | --- |
| `openssl genrsa -out KEYFILE 2048` | Generate a new RSA private key |
| `openssl rsa -in KEYFILE -pubout -out PUBFILE` | Extract the public key from a private key |
| `openssl rsa -in KEYFILE -out NEWKEYFILE` | Convert a private key to a different format |
| `openssl rand -hex 16` | Generate a random hex string |

## Certificate Signing

| Command | Description |
| --- | --- |
| `openssl ca -in CSRFILE -out CERTFILE` | Sign a certificate request |
| `openssl ca -config CONFIGFILE -in CSRFILE -out CERTFILE` | Sign a certificate request with a custom configuration |
| `openssl verify -CAfile CAFILE CERTFILE` | Verify a certificate against a CA file |

## Certificate Conversion

| Command | Description |
| --- | --- |
| `openssl pkcs12 -export -in CERTFILE -inkey KEYFILE -out PKCSFILE` | Convert a certificate and key to PKCS#12 format |
| `openssl pkcs12 -in PKCSFILE -out CERTFILE -nodes` | Extract a certificate and key from a PKCS#12 file |
| `openssl x509 -in CERTFILE -outform DER -out DERFILE` | Convert a certificate to DER format |
| `openssl x509 -in CERTFILE -outform PEM -out PEMFILE` | Convert a certificate to PEM format |

## Encryption and Decryption

| Command | Description |
| --- | --- |
| `openssl enc -aes-256-cbc -salt -in PLAINFILE -out ENCRYPTEDFILE` | Encrypt a file with AES-256-CBC |
| `openssl enc -d -aes-256-cbc -in ENCRYPTEDFILE -out DECRYPTEDFILE` | Decrypt a file encrypted with AES-256-CBC |
| `openssl dgst -sha256 FILE` | Calculate the SHA-256 hash of a file |
| `openssl dgst -md5 FILE` | Calculate the MD5 hash of a file |

## Miscellaneous

| Command | Description |
| --- | --- |
| `openssl version` | Display the OpenSSL version |
| `openssl s_client -connect HOST:PORT` | Connect to a server using SSL/TLS |
| `openssl s_server -accept PORT -cert CERTFILE -key KEYFILE` | Start an SSL/TLS server |
| `openssl speed` | Run benchmark tests on OpenSSL algorithms |
| `openssl ciphers -v` | List all available ciphers |
| `openssl rand -base64 32` | Generate a random base64 string |
| `openssl rand -base64 -out FILE 32` | Generate a random base64 string and save it to a file |
| `openssl rand -out FILE 32` | Generate a random binary string and save it to a file |
| `openssl rand -hex 32` | Generate a random hex string |
