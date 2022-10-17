---
title: MPPCOVER
section: 1
header: User Manual
footer: mppcover 1.0.1
date: August 6, 2022
---
## NAME
mppcover - display the album cover for the currently playing song

## SYNOPSIS
**mppcover** [OPTIONS] [DIR]

## DESCRIPTION

The *mppcover* command can be used to display the cover art of the
current track being played by MPD (Music Player Daemon).

DIR is the path to the MPD music library root directory, as defined in its
music_directory variable. Defaults to *$HOME/Music*.

## OPTIONS

**-h**
: Print usage information and exit

**-i filepath**
: Image Viewer to be used. Defaults to eom (Eye of MATE)

**-o 'options'**
: Command line options to pass to the Image Viewer

**-v**
: Print version number and exit

## AUTHORS

Written by Ronald Record github@ronrecord.com

## LICENSING

MPPCOVER is distributed under an Open Source license.
See the file LICENSE in the MPPCOVER source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPCOVER and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS

Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO

**listyt**(1), **mpplus**(1), **yt-dlp**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

