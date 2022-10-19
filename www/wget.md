---
tags:
    - wget
    - commands
    - linux
---

# Wget

Wget is a computer program that retrieves content from web servers. It is part of the GNU Project. Its name derives from "World Wide Web" and "get." It supports downloading via HTTP, HTTPS, and FTP.

Its features include recursive download, conversion of links for offline viewing of local HTML, and support for proxies. It appeared in 1996, coinciding with the boom of popularity of the Web, causing its wide use among Unix users and distribution with most major Linux distributions. Written in portable C, Wget can be easily installed on any Unix-like system. Wget has been ported to Microsoft Windows, macOS, OpenVMS, HP-UX, AmigaOS, MorphOS and Solaris. Since version 1.14 Wget has been able to save its output in the web archiving standard WARC format.

## Recursive download (current directory)

```bash
wget -r --no-parent http://firmware.openbsd.org/firmware/7.1/
```

## Recursive download (no robots follow)

```bash
wget -r --no-parent -e robots=off https://ftp.openbsd.org/pub/OpenBSD/songs/
```

## Quietly download a file

Continue where it left off if the connection fails.

The file will be downloaded to the current working directory.

```bash
wget -qc [URL]
```

## Specify a location to download the given file

```bash
wget -qcO [PATH] [URL]
```

## Download URL using the user agent string provided to the `-U` flag

```bash
wget -U 'Mozilla/5.0' [URL]
```

## See also

- [cURL](curl.md)
