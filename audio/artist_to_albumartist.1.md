---
title: ARTIST_TO_ALBUMARTIST
section: 1
header: User Manual
footer: artist_to_albumartist 1.0.0
date: September 21, 2022
---
## NAME
artist_to_albumartist - copies Artist tag to AlbumArtist for given files

## SYNOPSIS
**artist_to_albumartist** [--dry-run] files

## DESCRIPTION
The *artist_to_albumartist* command copies Artist tag (if present) to AlbumArtist (if not present) for given mp3/ogg/flac files.

**[Note:]** to run it recursively for all your files, you can use:

```
find DIRECTORY \
     \( -name "*.flac" -o -name "*.mp3" -o -name "*.ogg" \) \
     -exec ./artist_to_albumartist [--dry-run] {} \;
```

## COMMAND LINE OPTIONS

**--dry-run**
: says what it would do without doing anything

**files**
: files to modify

Without arguments displays a usage message and exits

## AUTHORS
Written by Andrzej Rybczak andrzej@rybczak.net

## LICENSING
ARTIST_TO_ALBUMARTIST is distributed under an Open Source license.
See the file LICENSE in the ARTIST_TO_ALBUMARTIST source distribution
for information on terms &amp; conditions for accessing and
otherwise using ARTIST_TO_ALBUMARTIST and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/mpcplus/issues

## SEE ALSO
**mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/mpcplus
