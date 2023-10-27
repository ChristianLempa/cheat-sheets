# SMTP (Simple Mail Transfer Protocol)

**SMTP (Simple Mail Transfer Protocol)** is a networking protocol for [mail](mail.md) transfer. It's used to send emails from a mail client to a mail server and between mail servers.

Server-to-Server communication is typically done over port `25`. Client-to-Server communication is typically done over port `587`. Alternatively, port `465` can be used for client-to-server communication with [TLS](../tls.md).

## Configuration

### SMTP Server

The SMTP server is a mail server that receives emails from a mail client and forwards them to their intended recipients. It's also responsible for receiving emails from other mail servers and delivering them to their intended recipients.

### SMTP Client

The SMTP client is a mail client that sends emails to a mail server for delivery. It's also responsible for receiving emails from other mail servers and delivering them to their intended recipients.

## Troubleshooting

[SMTP Troubleshooting Cheat Sheet](smtp-troubleshooting.md)

## References

- [SMTP (Simple Mail Transfer Protocol)](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)
