# EHLO Response Codes Cheat-Sheet

> Please note that the presence and specific **EHLO response codes** will depend on the **SMTP server software**, its version, and its configuration. The above table includes some commonly encountered **EHLO response codes**, but it may not cover every possible code or extension.

| EHLO Response Code | Description |
| --- | --- |
| 250 | Requested mail action okay, completed |
| 250-PIPELINING | Server supports command pipelining |
| 250-SIZE `<value>` | Server specifies maximum message size |
| 250-ETRN | Server supports the ETRN extension |
| 250-ENHANCEDSTATUSCODES | Server uses enhanced status codes |
| 250-8BITMIME | Server supports the 8BITMIME extension |
| 250-DSN | Server supports delivery status notifications (DSN) |
| 250-STARTTLS | Server supports TLS encryption |
| 250-AUTH `<authentication_types>` | Server specifies supported authentication types |
| 250-DELIVERBY | Server supports the DELIVERBY extension |
| 250-RSET | Server supports the RSET command |
| 250-HELP | Server provides help information |
| 250-BINARYMIME | Server supports binary MIME (Multipurpose Internet Mail Extensions) |
| 250-CHUNKING | Server supports chunking for message transmission |
| 250-EXPN | Server supports the EXPN command |
| 250-VRFY | Server supports the VRFY command |
| 250-X-EXPS `<extension>` | Server supports an additional extension |
| 250 X-LINK2STATE | Server provides link-related state information |
