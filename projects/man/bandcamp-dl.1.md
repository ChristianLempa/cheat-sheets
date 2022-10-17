---
title: BANDCAMP-DL
section: 1
header: User Manual
footer: bandcamp-dl 0.0.13
date: July 24, 2022
---
## NAME
bandcamp-dl - Download tracks and albums in a Bandcamp collection

## SYNOPSIS
**bandcamp-dl** [options] [URL ...]

## ARGUMENTS

- **URL** Bandcamp album/track URL

## OPTIONS

- **-h --help**               Show this screen.
- **-v --version**            Show version.
- **-d --debug**              Verbose logging.
- **--artist=<artist>**       The artist's slug (from the URL, --track or --album is required)
- **--track=<track>**         The track's slug (from the URL, for use with --artist)
- **--album=<album>**         The album's slug (from the URL, for use with --artist)
- **--template=<template>**   Output filename template.  [default: %{artist}/%{album}/%{track} - %{title}]
- **--base-dir=<dir>**        Base location of which all files are downloaded.
- **-f --full-album**         Download only if all tracks are available.
- **-o --overwrite**          Overwrite tracks that already exist. Default is False.
- **-n --no-art**             Skip grabbing album art.
- **-e --embed-lyrics**       Embed track lyrics (If available)
- **-g --group**              Use album/track Label as iTunes grouping.
- **-r --embed-art**          Embed album art (If available)
- **-y --no-slugify**         Disable slugification of track, album, and artist names.
- **-c --ok-chars=<chars>**   Specify allowed chars in slugify.  [default: - ~]
- **-s --space-char=<char>**  Specify the char to use in place of spaces.  [default: -]
- **-a --ascii-only**         Only allow ASCII chars (北京 (capital of china) -> bei-jing-capital-of-china)
- **-k --keep-spaces**        Retain whitespace in filenames
- **-u --keep-upper**         Retain uppercase letters in filenames

## DESCRIPTION

The *bandcamp-dl* command can be used to download tracks and albums from a Bandcamp collections. MusicPlayerPlus provides a convenience wrapper for *bandcamp-dl*, `/usr/share/musicplayerplus/calliope/bandcamp-download`.

## AUTHORS

*bandcamp-dl* is written and maintained by:

-   Iheanyi Ekechukwu
-   Anthony Forsberg
-   John Titor
-   Alex Bouffard
-   Pedro Lopes
-   Bendito999
-   Gabor Szabo
-   Vladde Nordholm
-   Simon W. Jackson
-   Yo'av Moshe
-   Mitchell Barron
-   Seppi
-   Andrew Sampson
-   Joseph Kahn
-   Diego Costa
-   Gal Schlezinger

*bandcamp-download* is written by Ronald Record github@ronrecord.com

## LICENSING
BANDCAMP-DL is distributed under an Open Source license.
See the file LICENSE in the BANDCAMP-DL source distribution
for information on terms &amp; conditions for accessing and
otherwise using BANDCAMP-DL and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**beet**(1), **mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

