# SMTP Protocol Troubleshooting

[SMTP (Simple Mail Transfer Protocol)](smtp.md) is a networking protocol for mail transfer. It's used to send emails from a mail client to a mail server and between mail servers.

## Troubleshooting

### Test SMTP Server connectivity

```bash
telnet smtp.example.com 25
```

### Test SMTP Server connectivity with TLS

```bash
openssl s_client -starttls smtp -connect smtp.example.com:587
```

### SMTP Commands

#### HELO

The HELO (or EHLO) command is a command used by the SMTP client when it initiates a connection with an SMTP server, to announce itself and establish communication.

```bash
EHLO example.com
```

In response to the HELO command, the SMTP server typically sends a reply code indicating the success or failure of the command. The server may also include additional information or instructions. Here's an example of an EHLO response:

```bash
250-FR3P281CA0133.outlook.office365.com Hello [***.***.***.***]
250-SIZE 157286400
250-PIPELINING
250-DSN
250-ENHANCEDSTATUSCODES
250-STARTTLS
250-8BITMIME
250-BINARYMIME
250-CHUNKING
250 SMTPUTF8
```

For more information about EHLO response codes see [EHLO Response Codes](ehlo-codes.md).

For more information about SMTP response codes see [SMTP Response Codes](smtp-codes.md).

#### AUTH

```smtp
AUTH LOGIN
<your-encoded-username>
<your-encoded-password>
```
