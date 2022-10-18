---
tags:
    - media type
categories:
    - other
---

# MIME

Multipurpose Internet Mail Extensions (MIME) is an Internet standard that extends the format of email messages to support text in character sets other than ASCII, as well as attachments of audio, video, images, and application programs. Message bodies may consist of multiple parts, and header information may be specified in non-ASCII character sets. Email messages with MIME formatting are typically transmitted with standard protocols, such as the Simple Mail Transfer Protocol (SMTP), the Post Office Protocol (POP), and the Internet Message Access Protocol (IMAP).

The MIME standard is specified in a series of requests for comments: RFC 2045, RFC 2046, RFC 2047, RFC 4288, RFC 4289 and RFC 2049. The integration with SMTP email is specified in RFC 1521 and RFC 1522.

Although the MIME formalism was designed mainly for SMTP, its content types are also important in other communication protocols. In the HyperText Transfer Protocol (HTTP) for the World Wide Web, servers insert a MIME header field at the beginning of any Web transmission. Clients use the content type or media type header to select an appropriate viewer application for the type of data indicated.

This cheat sheet lists some common MIME types for the Web. You can look in the [IANA/MIME Media Types registry](http://www.iana.org/assignments/media-types/index.html) which contains all registered MIME types.

## Introduction

- The MIME type registry associates particular filename extensions and filename pattern
- MIME (Multipurpose Internet Mail Extensions) type aka media type
- MIME types are defined and standardized in IETF's RFC 6838
- Indicates the nature and format of a document, file, or assortment of bytes.
- For file formats or format contents on the Internet

### Multi-format of MIME types

- [Markdown Table](https://tableconvert.com/html-to-markdown?data=https://quickref.me/mime#TableGenerator)
- [Template](https://tableconvert.com/html-to-template?data=https://quickref.me/mime#TableGenerator)
- [LaTeX Table](https://tableconvert.com/html-to-latex?data=https://quickref.me/mime#TableGenerator)
- [CSV](https://tableconvert.com/html-to-csv?data=https://quickref.me/mime#TableGenerator)
- [Excel](https://tableconvert.com/html-to-excel?data=https://quickref.me/mime#TableGenerator)
- [JSON Array](https://tableconvert.com/html-to-json?data=https://quickref.me/mime#TableGenerator)
- [HTML Table](https://tableconvert.com/html-to-html?data=https://quickref.me/mime#TableGenerator)
- [Insert SQL](https://tableconvert.com/html-to-sql?data=https://quickref.me/mime#TableGenerator)
- [YAML Sequence](https://tableconvert.com/html-to-yaml?data=https://quickref.me/mime#TableGenerator)
- [XML](https://tableconvert.com/html-to-xml?data=https://quickref.me/mime#TableGenerator)
- [ASCII](https://tableconvert.com/html-to-ascii?data=https://quickref.me/mime#TableGenerator)
- [MediaWiki Table](https://tableconvert.com/html-to-mediawiki?data=https://quickref.me/mime#TableGenerator)
- [AsciiDoc Table](https://tableconvert.com/html-to-asciidoc?data=https://quickref.me/mime#TableGenerator)
- [Jira Table](https://tableconvert.com/html-to-jira?data=https://quickref.me/mime#TableGenerator)
- [Textile Table](https://tableconvert.com/html-to-textile?data=https://quickref.me/mime#TableGenerator)
- [reStructuredText](https://tableconvert.com/html-to-restructuredtext?data=https://quickref.me/mime#TableGenerator)
- [PHP Array](https://tableconvert.com/html-to-php?data=https://quickref.me/mime#TableGenerator)
- [Ruby Array](https://tableconvert.com/html-to-ruby?data=https://quickref.me/mime#TableGenerator)
- [ASP Array](https://tableconvert.com/html-to-asp?data=https://quickref.me/mime#TableGenerator)
- [ActionScript](https://tableconvert.com/html-to-actionscript?data=https://quickref.me/mime#TableGenerator)
- [BBCode](https://tableconvert.com/html-to-bbcode?data=https://quickref.me/mime#TableGenerator)
- [PDF](https://tableconvert.com/html-to-pdf?data=https://quickref.me/mime#TableGenerator)
- [JPEG](https://tableconvert.com/html-to-jpeg?data=https://quickref.me/mime#TableGenerator)

## Lists of MIME types

### Common MIME (Media) types
| Extension       | Kind of document                                 | MIME Type \(Content Type\)                                                                                                               |
|-----------------|--------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| \.aac           | AAC audio                                        | audio/aac                                                                                                                                |
| \.abw           | AbiWord document                                 | application/x\-abiword                                                                                                                   |
| \.arc           | Archive document \(multiple files embedded\)     | application/x\-freearc                                                                                                                   |
| \.avi           | AVI: Audio Video Interleave                      | video/x\-msvideo                                                                                                                         |
| \.azw           | Amazon Kindle eBook format                       | application/vnd\.amazon\.ebook                                                                                                           |
| \.bin           | Any kind of binary data                          | application/octet\-stream                                                                                                                |
| \.bmp           | Windows OS/2 Bitmap Graphics                     | image/bmp                                                                                                                                |
| \.bz            | BZip archive                                     | application/x\-bzip                                                                                                                      |
| \.bz2           | BZip2 archive                                    | application/x\-bzip2                                                                                                                     |
| \.csh           | C\-Shell script                                  | application/x\-csh                                                                                                                       |
| \.css           | Cascading Style Sheets \(CSS\)                   | text/css                                                                                                                                 |
| \.csv           | Comma\-separated values \(CSV\)                  | text/csv                                                                                                                                 |
| \.doc           | Microsoft Word                                   | application/msword                                                                                                                       |
| \.docx          | Microsoft Word \(OpenXML\)                       | application/vnd\.openxmlformats\-officedocument\.wordprocessingml\.document                                                              |
| \.eot           | MS Embedded OpenType fonts                       | application/vnd\.ms\-fontobject                                                                                                          |
| \.epub          | Electronic publication \(EPUB\)                  | application/epub\+zip                                                                                                                    |
| \.gz            | GZip Compressed Archive                          | application/gzip                                                                                                                         |
| \.gif           | Graphics Interchange Format \(GIF\)              | image/gif                                                                                                                                |
| \.htm \.html    | HyperText Markup Language \(HTML\)               | text/html                                                                                                                                |
| \.ico           | Icon format                                      | image/vnd\.microsoft\.icon                                                                                                               |
| \.ics           | iCalendar format                                 | text/calendar                                                                                                                            |
| \.jar           | Java Archive \(JAR\)                             | application/java\-archive                                                                                                                |
| \.jpeg \.jpg    | JPEG images                                      | image/jpeg                                                                                                                               |
| \.js            | JavaScript                                       | text/javascript                                                                                                                          |
| \.json          | JSON format                                      | application/json                                                                                                                         |
| \.jsonld        | JSON\-LD format                                  | application/ld\+json                                                                                                                     |
| \.mid \.midi    | Musical Instrument Digital Interface \(MIDI\)    | audio/midi audio/x\-midi                                                                                                                 |
| \.mjs           | JavaScript module                                | text/javascript                                                                                                                          |
| \.mp3           | MP3 audio                                        | audio/mpeg                                                                                                                               |
| \.mpeg          | MPEG Video                                       | video/mpeg                                                                                                                               |
| \.mpkg          | Apple Installer Package                          | application/vnd\.apple\.installer\+xml                                                                                                   |
| \.odp           | OpenDocument presentation document               | application/vnd\.oasis\.opendocument\.presentation                                                                                       |
| \.ods           | OpenDocument spreadsheet document                | application/vnd\.oasis\.opendocument\.spreadsheet                                                                                        |
| \.odt           | OpenDocument text document                       | application/vnd\.oasis\.opendocument\.text                                                                                               |
| \.oga           | OGG audio                                        | audio/ogg                                                                                                                                |
| \.ogv           | OGG video                                        | video/ogg                                                                                                                                |
| \.ogx           | OGG                                              | application/ogg                                                                                                                          |
| \.opus          | Opus audio                                       | audio/opus                                                                                                                               |
| \.otf           | OpenType font                                    | font/otf                                                                                                                                 |
| \.png           | Portable Network Graphics                        | image/png                                                                                                                                |
| \.pdf           | Adobe Portable Document Format \(PDF\)           | application/pdf                                                                                                                          |
| \.php           | Hypertext Preprocessor \(Personal Home Page\)    | application/php                                                                                                                          |
| \.ppt           | Microsoft PowerPoint                             | application/vnd\.ms\-powerpoint                                                                                                          |
| \.pptx          | Microsoft PowerPoint \(OpenXML\)                 | application/vnd\.openxmlformats\-officedocument\.presentationml\.presentation                                                            |
| \.rar           | RAR archive                                      | application/vnd\.rar                                                                                                                     |
| \.rtf           | Rich Text Format \(RTF\)                         | application/rtf                                                                                                                          |
| \.sh            | Bourne shell script                              | application/x\-sh                                                                                                                        |
| \.svg           | Scalable Vector Graphics \(SVG\)                 | image/svg\+xml                                                                                                                           |
| \.swf           | Small web format \(SWF\) or Adobe Flash document | application/x\-shockwave\-flash                                                                                                          |
| \.tar           | Tape Archive \(TAR\)                             | application/x\-tar                                                                                                                       |
| \.tif \.tiff    | Tagged Image File Format \(TIFF\)                | image/tiff                                                                                                                               |
| \.ts            | MPEG transport stream                            | video/mp2t                                                                                                                               |
| \.ttf           | TrueType Font                                    | font/ttf                                                                                                                                 |
| \.txt           | Text, \(generally ASCII or ISO 8859\-n\)         | text/plain                                                                                                                               |
| \.vsd           | Microsoft Visio                                  | application/vnd\.visio                                                                                                                   |
| \.wav           | Waveform Audio Format                            | audio/wav                                                                                                                                |
| \.weba          | WEBM audio                                       | audio/webm                                                                                                                               |
| \.webm          | WEBM video                                       | video/webm                                                                                                                               |
| \.webp          | WEBP image                                       | image/webp                                                                                                                               |
| \.woff          | Web Open Font Format \(WOFF\)                    | font/woff                                                                                                                                |
| \.woff2         | Web Open Font Format \(WOFF\)                    | font/woff2                                                                                                                               |
| \.xhtml         | XHTML                                            | application/xhtml\+xml                                                                                                                   |
| \.xls           | Microsoft Excel                                  | application/vnd\.ms\-excel                                                                                                               |
| \.xlsx          | Microsoft Excel \(OpenXML\)                      | application/vnd\.openxmlformats\-officedocument\.spreadsheetml\.sheet                                                                    |
| \.xml           | XML                                              | application/xml if not readable from casual users \(RFC 3023, section 3\) text/xml if readable from casual users \(RFC 3023, section 3\) |
| \.xul           | XUL                                              | application/vnd\.mozilla\.xul\+xml                                                                                                       |
| \.zip           | ZIP archive                                      | application/zip                                                                                                                          |
| \.3gp           | 3GPP audio/video container                       | video/3gpp audio/3gpp if it doesn't contain video                                                                                        |
| \.3g2           | 3GPP2 audio/video container                      | video/3gpp2 audio/3gpp2 if it doesn't contain video                                                                                      |
| \.7z            | 7\-zip archive                                   | application/x\-7z\-compressed                                                                                                            |
| \.markdown \.md | Markdown File                                    | text/markdown                                                                                                                            |
