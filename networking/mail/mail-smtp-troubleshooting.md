# SMTP Troubleshooting Cheat Sheet

[SMTP (Simple Mail Transfer Protocol)](mail-smtp.md) is a networking protocol for mail transfer. It's used to send emails from a mail client to a mail server and between mail servers.

## Test SMTP Server connectivity

```bash
telnet smtp.example.com 25
```

## Test SMTP Server connectivity with STARTTLS

```bash
openssl s_client -starttls smtp -ign_eof -crlf -connect smtp.example.com:587
```

## HELO

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

*For more information about EHLO response codes see [EHLO Response Codes](ehlo-codes.md), and for SMTP response codes see [SMTP Response Codes](smtp-codes.md).*

## Authentication

SMTP servers typically require authentication before allowing a user to send mail. Some authentication methods, such as `LOGIN` and `PLAIN`, are supported by default, while others may need to be enabled by the server administrator.

```bash
AUTH LOGIN
your-base64encoded-username
your-base64encoded-password
```

To encode a string in base64, you can use the `base64` command:

```bash
echo -n "username" | base64
```

## Send Email

To test sending an email using the `MAIL FROM`, `RCPT TO`, and `DATA` commands:

```bash
MAIL FROM: <sender@example.com>
RCPT TO: <recipient@example.com>
DATA
Subject: This is the subject line

This is the message body.
You can write multiple lines.
.
```
