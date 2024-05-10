# SMTP Response Codes Cheat-Sheet

| Status Code | Description |
| --- | --- |
| 211 | System status or system help response |
| 214 | Help message |
| 220 | Service ready |
| 221 | Service closing transmission channel |
| 235 | Authentication successful |
| 250 | Requested mail action completed |
| 251 | User not local; will forward |
| 252 | Cannot verify the user; will attempt delivery |
| 354 | Start mail input; end with `<CRLF>.<CRLF>` |
| 421 | Service not available, closing transmission channel |
| 450 | Requested action not taken - mailbox unavailable |
| 451 | Requested action aborted: local error in processing |
| 452 | Requested action not taken - insufficient system storage |
| 500 | Syntax error, command unrecognized |
| 501 | Syntax error in parameters or arguments |
| 502 | Command not implemented |
| 503 | Bad sequence of commands |
| 504 | Command parameter not implemented |
| 550 | Requested action not taken - mailbox unavailable |
| 551 | User not local; please try `<forward-path>` |
| 552 | Requested mail action aborted - exceeded storage allocation |
| 553 | Requested action not taken - mailbox name not allowed |
| 554 | Transaction failed |
