---
title: MPPDL
section: 1
header: User Manual
footer: mppdl 1.0.1
date: August 11, 2022
---
## NAME
mppdl - download audio tracks from Bandcamp, Soundcloud, or a URL

## SYNOPSIS
**mppdl** [-a album] [-A artist] [-d music_dir] [-i] [-I] [-f fmt] [-l] [-t track] [-T title] bandcamp|soundcloud|downloads|URL

## DESCRIPTION

The *mppdl* command can be used to download audio tracks in a Bandcamp
collection, Soundcloud favorites, or a specified URL using `yt-dlp`.
Bandcamp collections are downloaded into *music_directory/Bandcamp/*,
Soundcloud favorites are downloaded into *music_directory/Soundcloud/*, and
audio in the specified URL is downloaded into *music_directory/Downloads/*.
The *music_directory* path is that specified in `$HOME/.config/mpd/mpd.conf`
or `$HOME/.config/mpprc`. By default this is `$HOME/Music/`.

If a Beets import is specified with the `-i` option then the import is
performed non-interactively. Beets tries to identify the audio using
metadata and filenames but may perform the matching incorrectly. When
automatically importing downloaded audio in this manner, verify the
import matching was properly performed. If an interactive Beets import
is preferred then do not use the `-i` option to `mppdl` and perform
the Beets import manually after the download completes.

Import already downloaded songs into Beets with the `-I` option. Restrict
the import to Bandcamp downloads with `mppdl -I bandcamp`, Soundcloud downloads
with `mppdl -I soundcloud`, URL downloaded songs with `mppdl -I downloads`, and
import all previously downloaded songs from Bandcamp, Soundcloud, or
a URL with `mppdl -I`.

## OPTIONS

**-a 'album'**
: saves the download in the subdirectory 'album'

**-A 'artist'**
: saves the download with filename 'artist'-'title'.m4a

**-d 'music_dir'**
: overrides the 'music_dir' location specified in config files

**-i**
: indicates import audio into Beets after download completes

**-I**
: indicates import previously downloaded audio into Beets

**-f 'fmt'**
: saves the download in 'fmt' format (default m4a)

**-t 'track'**
: saves the download with filename 'track'-'artist'-'title'.m4a

**-T 'title'**
: saves the download with filename 'artist'-'title'.m4a

**-l**
: indicates list available formats and info on URL

**-u**
: displays this usage message and exits

The argument *bandcamp*, *soundcloud*, or *URL* indicates:

- Download Bandcamp collections
- Download Soundcloud favorites
- Download audio in URL

## AUTHORS

Written by Ronald Record github@ronrecord.com

## LICENSING

MPPDL is distributed under an Open Source license.
See the file LICENSE in the MPPDL source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPDL and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS

Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO

**beet**(1), **mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

