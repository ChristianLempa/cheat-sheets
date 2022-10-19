# cURL

cURL (pronounced like "curl") is a computer software project providing a library (libcurl) and command-line tool (curl) for transferring data using various network protocols. The name stands for "Client URL".

## Process a single GET request, and show its output on stdout

```bash
curl http://path.to.the/file
```

## Download a file and specify a new filename

```bash
curl http://example.com/file.zip -o new_file.zip
```

## Download multiple files

```bash
curl -O URLOfFirstFile -O URLOfSecondFile
```

## Download all sequentially-numbered files (1-24)

```bash
curl http://example.com/pic[1-24].jpg
```

## Download a file and follow redirects

```bash
curl -L http://example.com/file
```

## Download a file and pass HTTP Authentication

```bash
curl -u username:password URL
```

## Download a file with a Proxy

```bash
curl -x proxysever.server.com:PORT http://addressiwantto.access
```

## Download a file from FTP

```bash
curl -u username:password -O ftp://example.com/pub/file.zip
```

## Get an FTP directory listing

```bash
curl ftp://username:password@example.com
```

## Resume a previously failed download

```bash
curl -C - -o partial_file.zip http://example.com/file.zip
```

## Fetch only the HTTP headers from a response

```bash
curl -I http://example.com
```

## Fetch your external IP and network info as JSON

```bash
curl http://ifconfig.me/all/json
```

## Limit the rate of a download

```bash
curl --limit-rate 1000B -O http://path.to.the/file
```

## POST to a form

```bash
curl -F "name=user" -F "password=test" http://example.com
```

## POST JSON Data

```bash
curl -H "Content-Type: application/json" -X POST -d '{"user":"bob","pass":"123"}' http://example.com
```

## POST data from the standard in / share data on sprunge.us

```bash
curl -F 'sprunge=<-' sprunge.us
```

## See also

- [Wget](wget.md)
