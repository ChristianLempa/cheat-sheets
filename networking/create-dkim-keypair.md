# Generate a DKIM Keypair
We use the tool OpenSSL ([[openssl]]]) to generate a DKIM private and public keypair.

`openssl genrsa -out dkim_private.pem 2048`

`openssl rsa -in dkim_private.pem -pubout -outform der 2>/dev/null | openssl base64 -A`

