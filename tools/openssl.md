# OpenSSL Cheat-Sheet

## Certificate Management

| Command | Description |
| --- | --- |
| `openssl req -new -key <key> -out <csr>` | Generate a new certificate signing request |
| `openssl req -x509 -key <key> -in <csr> -out <cert>` | Generate a self-signed certificate |
| `openssl x509 -in <cert> -text -noout` | Display the details of a certificate |
| `openssl x509 -in <cert> -pubkey -noout` | Extract the public key from a certificate |
| `openssl x509 -in <cert> -fingerprint -noout` | Display the fingerprint of a certificate |

## Key Management

| Command | Description |
| --- | --- |
| `openssl genrsa -out <key> 2048` | Generate a new RSA private key |
| `openssl rsa -in <key> -pubout -out <pub_key>` | Extract the public key from a private key |
| `openssl rsa -in <key> -out <new_key>` | Convert a private key to a different format |
| `openssl rand -hex 16` | Generate a random hex string |

## Certificate Signing

| Command | Description |
| --- | --- |
| `openssl ca -in <csr> -out <cert>` | Sign a certificate request |
| `openssl ca -config <config> -in <csr> -out <cert>` | Sign a certificate request with a custom configuration |
| `openssl verify -CAfile <ca> <cert>` | Verify a certificate against a CA file |

## Certificate Conversion

| Command | Description |
| --- | --- |
| `openssl pkcs12 -export -in <cert> -inkey <key> -out <file>` | Convert a certificate and key to PKCS#12 format |
| `openssl pkcs12 -in <file> -out <cert> -nodes` | Extract a certificate and key from a PKCS#12 file |
| `openssl x509 -in <cert> -outform DER -out <file>` | Convert a certificate to DER format |
| `openssl x509 -in <cert> -outform PEM -out <file>` | Convert a certificate to PEM format |

## Encryption and Decryption

| Command | Description |
| --- | --- |
| `openssl enc -aes-256-cbc -salt -in <file> -out <encrypted_file>` | Encrypt a file with AES-256-CBC |
| `openssl enc -d -aes-256-cbc -in <file> -out <decrypted_file>` | Decrypt a file encrypted with AES-256-CBC |
| `openssl dgst -sha256 FILE` | Calculate the SHA-256 hash of a file |
| `openssl dgst -md5 FILE` | Calculate the MD5 hash of a file |

## Miscellaneous

| Command | Description |
| --- | --- |
| `openssl version` | Display the OpenSSL version |
| `openssl s_client -connect <host>:<port>` | Connect to a server using SSL/TLS |
| `openssl s_server -accept <port> -cert <cert> -key <key>` | Start an SSL/TLS server |
| `openssl speed` | Run benchmark tests on OpenSSL algorithms |
| `openssl ciphers -v` | List all available ciphers |
| `openssl rand -base64 32` | Generate a random base64 string |
| `openssl rand -base64 -out <file> 32` | Generate a random base64 string and save it to a file |
| `openssl rand -out <file> 32` | Generate a random binary string and save it to a file |
| `openssl rand -hex 32` | Generate a random hex string |
