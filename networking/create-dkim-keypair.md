# Generate a DKIM Keypair

DomainKeys Identified Mail (DKIM) is an email authentication method designed to detect forged sender addresses in email (email spoofing), a technique often used in phishing and email spam.

DKIM allows the receiver to check that an email claimed to have come from a specific domain was indeed authorized by the owner of that domain. It achieves this by affixing a digital signature, linked to a domain name, to each outgoing email message. The recipient system can verify this by looking up the sender's public key published in the [DNS](dns.md). A valid signature also guarantees that some parts of the email (possibly including attachments) have not been modified since the signature was affixed. Usually, DKIM signatures are not visible to end-users, and are affixed or verified by the infrastructure rather than the message's authors and recipients.

DKIM is an Internet Standard.

## Generate DKIM key pair

Use the [OpenSSL](../tools/openssl.md) tool to generate a DKIM private and public keypair.

```shell
openssl genrsa -out dkim_private.pem 2048
openssl rsa -in dkim_private.pem -pubout -outform der 2>/dev/null | openssl base64 -A
```

