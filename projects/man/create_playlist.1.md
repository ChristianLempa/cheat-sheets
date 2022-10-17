---
title: CREATE_PLAYLIST
section: 1
header: User Manual
footer: create_playlist 1.0.0
date: July 24, 2022
---
## NAME
create_playlist - create a playlist of songs matching a Beets query

## SYNOPSIS
**create_playlist** [-n playlist-name] [-q beets-query] [-ou]

Where:

- *-n 'playlist-name'* specifies the playlist name
- *-q 'beets-query'* specifies the Beets query to use
- *-o* indicates overwrite any pre-existing playlist of same name
- *-u* displays this usage message and exits

## DESCRIPTION

The *create_playlist* command can be used to create an MPD playlist
of songs matching a Beets query. For example, to create a playlist
of all songs with the word "love" in their name or path (e.g. artist,
album, title), issue the command:

```
create_playlist -n LoveList -q love
```

A new playlist named "LoveList" will be created containing all the
songs in the music library that match the string "love" (case insensitive).

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
CREATE_PLAYLIST is distributed under an Open Source license.
See the file LICENSE in the CREATE_PLAYLIST source distribution
for information on terms &amp; conditions for accessing and
otherwise using CREATE_PLAYLIST and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**beet**(1), **mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

