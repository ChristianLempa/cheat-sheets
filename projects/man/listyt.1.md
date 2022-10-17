---
title: LISTYT
section: 1
header: User Manual
footer: listyt 1.0.1
date: August 6, 2022
---
## NAME

listyt - list YouTube video titles and urls

## SYNOPSIS

**listyt** [-c|-f|-p|-v user] [url]

## DESCRIPTION

The *listyt* command can be used to list video titles and urls of provided
YouTube URL or, if user options are provided, list user channel subscriptions,
featured videos, playlists, or uploads.

## OPTIONS

**-c 'user'**
: list channel subscriptions for YouTube user 'user'

**-f 'user'**
: list featured video for YouTube user 'user'

**-p 'user'**
: list playlists for YouTube user 'user'

**-v 'user'**
: list video uploads for YouTube user 'user'

**-u**
: displays this usage message and exits

**'url'**
: list video title(s) and url(s) at YouTube URL

## EXAMPLES

- `listyt -c doctorfree`
- `listyt -f doctorfree`
- `listyt -p doctorfree`
- `listyt -v doctorfree`
- `listyt https://youtube.com/playlist?list=PLh3A0cnoWYswaNiG_9WGX2q5L5GpxUZuF`

## AUTHORS

Written by Ronald Record github@ronrecord.com

## LICENSING

LISTYT is distributed under an Open Source license.
See the file LICENSE in the LISTYT source distribution
for information on terms &amp; conditions for accessing and
otherwise using LISTYT and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS

Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO

**yt-dlp**(1), **mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

