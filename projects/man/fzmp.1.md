---
title: FZMP
section: 1
header: User Manual
footer: fzmp 1.0.0
date: March 24, 2022
---
## NAME
fzmp - list and search songs in the MPD music library using the `fzf` fuzzy finder

## SYNOPSIS
**fzmp** [OPTIONS]

## DESCRIPTION
The *fzmp* command lists and searches for songs in an MPD library by
artist, album, or playlist using the `fzf` fuzzy finder.

## COMMAND LINE OPTIONS

**-h --help**
: print this help

**-a --artist**
: search artist then filter by album (or F3 when running)

**-A --all**
: search all songs in the library (or F2 when running)

**-g --genre**
: list genres (or F4 when running)

**-P --playlists**
: list saved playlists (or F5 when running)

**-p --playlist**
: search the current playlist (or F1 when running)

Playlist view has the following keybinds:

**&gt;**
: go to the next song in the playlist

**&lt;**
: go to the previous song in the playlist

**Ctrl-d**
: delete the selected songs from the playlist

**Ctrl-s**
: save current playlist

**Ctrl-p**
: toggle play/pause

## CONFIGURATION:
A configuration file can be defined at $HOME/.config/mpcplus/fzmp.conf

If a line begins with '#' it is treated as a comment and ignored

The configuration file reads the following options:

**default_view**
: Must be 'artists' 'songs' 'playlist' 'playlists' or 'genres'

**full_song_format**
: A format string to be passed directly to `mpc format -f` in 'playlist' and 'all' views. Defaults to:

```
    [[[%artist% / ][[(%date%) ]%album% / ][[%track% - ][%title%]]]|%file%]
```

    For colorized output try:

```
    [[[\e\[32m%artist%\e\[0m / ][\e\[31m[(%date%) ]%album%\e\[0m / ][\e\[34m[%track% - ][%title%]\e\[0m]]|%file%]
```

**playlist_view_key**
: (default F1)

**track_view_key**
: (default F2)

**artist_view_key**
: (default F3)

**genre_view_key**
: (default F4)

**playlists_view_key**
: (default F5)

**findadd_key**
: Adds all songs under the cursor by artist/genre/album (default ctrl-space)

**fzf_options**
: Command line options to be passed directly to fzf.

    Changing this will override the default options:

```
      --height='100%' +s -e -i --reverse --cycle
```

    To use the jump feature of fzf you can try:

```
      --bind=`:jump --height='100%' +s -e -i --reverse --cycle
```

    It also helps to have a bind for toggle-all:

```
      --bind=ctrl-t:toggle-all --bind=`:jump --height=100% +s -e -i --reverse --cycle
```

Individual sessions can override with the environment variable FZMP_FZF_OPTIONS

`fzmp` will also inherit options from FZF_DEFAULT_OPTS

## AUTHORS
Written by Daniel F Gray DanielFGray@gmail.com

Modified and adapted by Ronald Record github@ronrecord.com

## LICENSING
FZMP is distributed under an Open Source license.
See the file LICENSE in the FZMP source distribution
for information on terms &amp; conditions for accessing and
otherwise using FZMP and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

