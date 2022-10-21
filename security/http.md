# HTTP

## HTTP Authentication Types

### Digest Authentication (uses htdigest)

***-->susceptible to MITM attack!***

### Integrated Windows Authentication

***-->will not function over proxy***

### Form-Based Authentication

***-->not inherently encrypted, often poor implimentation***

## HTTP Response Codes

### Informational Response Codes (1xx)

| Response | Description |
|----------|-------------|
| 100 | Continue |
| 101 | Switching Protocols |
| 102 | Processing |

### Success Response Codes (2xx)

| Response | Description            | Response | Description       |
|----------|------------------------|----------|-------------------|
| 200      | OK                     | 206      | Partial Content   |
| 201      | Created                | 207      | Multi-status      |
| 202      | Accepted               | 208      | Already Reported  |
| 203      | Non-authoritative Info | 226      | IM Used           |
| 204      | No Content             | 250      | Low Storage Space |
| 205      | Reset Content | | |

### Redirection Response Codes (3xx)

| Response | Description            | Response | Description        |
|----------|------------------------|----------|--------------------|
| 300      | Multiple Choices       | 304      | Not Modified       |
| 301      | Moved Permanently      | 305      | Use Proxy          |
| 302      | Found                  | 307      | Temporary Redirect |
| 303      | See Other              | 308      | Permanent Redirect |

### Client Error Response Codes (4xx)

| Response | Description            | Response | Description        |
|----------|------------------------|----------|--------------------|
| 400      | Multiple Choices       | 410      | Not Modified       |
| 401      | Moved Permanently      | 411      | Use Proxy          |
| 402      | Found                  | 412      | Temporary Redirect |
| 403      | See Other              | 413      | Permanent Redirect |
| 404      | Multiple Choices       | 414      | Not Modified       |
| 405      | Moved Permanently      | 415      | Use Proxy          |
| 406      | Found                  | 416      | Temporary Redirect |
| 407      | See Other              | 417      | Permanent Redirect |
| 408      | Found                  | 418      | Temporary Redirect |
| 409      | See Other    | | | 

### Server Error Response Codes (5xx)

| Response | Description             | Response | Description                   |
|----------|-------------------------|----------|-------------------------------|
| 500      | Internal Server Error   | 508      | Loop Detected                 |
| 501      | Not Implemented         | 509      | Bandwidth Limited             |
| 502      | Bad Gateway             | 510      | Not Extended                  |
| 503      | Service Unavailable     | 511      | Network Auth Required         |
| 504      | Gateway Timeout         | 550      | Permission Denied             |
| 505      | HTTP Ver Not Supported  | 551      | Option Not Supported          |
| 506      | Variant Also Negotiates | 598      | Nework Read Timeout Error     |
| 507      | Insufficient Storage    | 599      | Network Connect Timeout Error |
