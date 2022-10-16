---
title: MPCINIT
section: 1
header: User Manual
footer: mpcinit 1.0.0
date: September 21, 2022
---
## NAME
mpcinit - performs one-time mpcplus initialization

## SYNOPSIS
**mpcinit** [-o] [-q] [-r] [-U] [-y] [-u] [mpd|sync]

## DESCRIPTION
The *mpcinit* command copies and configures default mpcplus
configuration files in `$HOME/.config/`. Some effort is made to identify the
music library location (default: $HOME/Music/).

Invoked with the `mpd` argument, *mpcinit mpd* activates the Music Player
Daemon (MPD) and deactivates the Mopidy music server and Mopidy extensions.

Invoked with the `sync` argument, *mpcinit sync* synchronizes
mpcplus configuration across all configuration files.

## COMMAND LINE OPTIONS

**-o**
: indicates overwrite any pre-existing configuration

**-q**
: indicates quiet execution, no status messages

**-y**
: indicates answer 'yes' to all and proceed

**-u**
: displays this usage message and exits

**mpd**
: activates the MPD music server

**sync**
: synchronizes mpcplus configuration across configs

*mpcinit* must be run as the mpcplus user, not root.

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPCINIT is distributed under an Open Source license.
See the file LICENSE in the MPCINIT source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPCINIT and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/mpcplus/issues

## SEE ALSO
**mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/mpcplus
