# Certutil

| Command | Description |
| --- | --- |
| `certutil -store MY` | List personal certificates |
| `certutil -store ROOT` | List root certificates |
| `certutil -store CA` | List intermediate certificates |
| `certutil -addstore -f "ROOT" new-root-certificate.crt` | Add a root certificate |
| `certutil -delstore "ROOT" serial-number-hex` | Remove a root certificate |
| `certutil -addstore -f "CA" new-intermediate-certificate.crt` | Add an intermediate certificate |
| `certutil -delstore "CA" serial-number-hex` | Remove an intermediate certificate |
| `certutil -addstore -f "MY" new-personal-certificate.pfx` | Add a personal certificate |
| `certutil -delstore "MY" serial-number-hex` | Remove a personal certificate |
| `certutil -dump certificate.crt` | Display certificate information |
| `certutil -encode certificate.crt encoded-certificate.txt` | Encode a certificate |
| `certutil -decode encoded-certificate.txt decoded-certificate.crt` | Decode a certificate |
| `certutil -hashfile file.txt SHA256` | Calculate the SHA256 hash of a file |
