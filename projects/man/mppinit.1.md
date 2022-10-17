---
title: MPPINIT
section: 1
header: User Manual
footer: mppinit 1.0.0
date: March 24, 2022
---
## NAME
mppinit - performs one-time MusicPlayerPlus initialization

## SYNOPSIS
**mppinit** [-a] [-b] [-d] [-e] [-l music_dir] [-o] [-q] [-r] [-U] [-y] [-u] [bandcamp | import | kitty | metadata | mopidy | mpd | navidrome | soundcloud | sync | yams]

## DESCRIPTION
The *mppinit* command copies and configures default MusicPlayerPlus
configuration files in `$HOME/.config/` and installs required Python
modules if not already installed. Some effort is made to identify the
music library location (default: $HOME/Music/). The music library location
can be specified on the command line with `mppinit -l /path/to/library`.

Invoked with the `bandcamp` argument, *mppinit bandcamp* downloads the
albums in your Bandcamp collections. A valid Bandcamp username must be
configured in `$HOME/.config/calliope/calliope.conf`. The Bandcamp albums
are downloaded to the `MUSIC_DIR` folder configured in
`$HOME/.config/mpprc` in a `Bandcamp` sub-folder.

Invoked with the `soundcloud` argument, *mppinit soundcloud* downloads the
favorites in your Soundcloud account. A valid Soundcloud user slug must be
provided at the prompt. The Soundcloud favorites are downloaded to the
`MUSIC_DIR` folder configured in `$HOME/.config/mpprc`
in a `Soundcloud` sub-folder.

Invoked with the `import` argument, *mppinit import* imports the music
library to the Beets media management system.

Invoked with the `kitty` argument, *mppinit kitty* installs the Kitty
terminal emulator used as the default terminal in MusicPlayerPlus.

Invoked with the `metadata` argument, *mppinit metadata* analyzess the
MPD music library and creates a song similarity database for playlist
creation. If accompanied by the `-e` argument, Essentia is used to
analyze, extract, and update the Beets library with acoustic information.
If accompanied by the `-a` argument, AcousticBrainz is used to retrieve
audio information rather than analyzing audio files with Essentia.

Invoked with the `mopidy` argument, *mppinit mopidy* installs the Mopidy
music server and several Mopidy extensions. The user MPD service is
deactivated and the Mopidy system service is activated.

Invoked with the `mpd` argument, *mppinit mpd* activates the Music Player
Daemon (MPD) and deactivates the Mopidy music server and Mopidy extensions.

Invoked with the `navidrome` argument, *mppinit navidrome* installs the
Navidrome music server and streamer. The Navidrome user system service
is activated. To install a specified version of Navidrome, use the command
`mppinit navidrome <version>`.

Invoked with the `sync` argument, *mppinit sync* synchronizes
MusicPlayerPlus configuration across all configuration files.

## COMMAND LINE OPTIONS

**-a**
: indicates use AcousticBrainz to retrieve audio information rather than using Essentia to analyze audio files

**-b**
: indicates use Blissify to analyze audio information rather than using Essentia to analyze audio files

**-d**
: indicates install latest Beets development branch rather than the latest stable release (for testing purposes)

**-e**
: indicates use Essentia to analyze audio information

**-l music_dir**
: specifies the location of the music library

**-o**
: indicates overwrite any pre-existing configuration

**-q**
: indicates quiet execution, no status messages

**-r**
: indicates remove service rather than initialize service. supported service removals: mopidy navidrome

**-U**
: indicates do not upgrade installed Python modules

**-y**
: indicates answer 'yes' to all and proceed

**-u**
: displays usage message and exits

**import**
: performs a Beets music library import

**metadata**
: performs a Beets library metadata update

**mopidy**
: Installs Mopidy and several extensions, deactivates MPD, activates Mopidy

**mpd**
: Activates MPD, deactivates Mopidy

**navidrome [version]**
: Installs, configures, and activates Navidrome music server/streamer

**sync**
: synchronizes MusicPlayerPlus configuration across configs

*mppinit* must be performed before a *sync*, *kitty*, *metadata*, *mopidy*, *mpd*, *navidrome*, *bandcamp*, *soundcloud*, or *import*

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPPINIT is distributed under an Open Source license.
See the file LICENSE in the MPPINIT source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPINIT and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpplus**(1), **mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus
