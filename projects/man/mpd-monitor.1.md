---
title: MPD-MONITOR
section: 1
header: User Manual
footer: mpd-monitor 1.0.1
date: September 14, 2022
---
## NAME
mpd-monitor - display info on Music Player Daemon (MPD) currently playing song

## SYNOPSIS
**mpd-monitor** [-c] [-g] [-k] [-q] [-s] [-t] [-T] [-u]

## DESCRIPTION

The *mpd-monitor* command can be used to display information on the track currently being played by MPD (Music Player Daemon). The `mpcplus` key binding `Alt-m` can be used to display a terminal window running `mpd-monitor`. If no song is currently being played then `mpd-monitor` silently exits. When MPD changes songs `mpd-monitor` automatically updates the information being displayed.

## OPTIONS

**-c**
: indicates use console mode

**-g**
: indicates use Gnome terminal emulator

**-k**
: Indicates use Kitty terminal emulator

**-q**
: Indicates quiet mode

**-s**
: Indicates use Simple terminal emulator

**-t**
: Indicates use Tilix terminal emulator

**-T**
: Indicates use a terminal emulator, no console mode

**-u**
: Displays this usage message and exits

## AUTHORS

Written by Ronald Record github@ronrecord.com

## LICENSING

MPD-MONITOR is distributed under an Open Source license.
See the file LICENSE in the MPD-MONITOR source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPD-MONITOR and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS

Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO

**mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

