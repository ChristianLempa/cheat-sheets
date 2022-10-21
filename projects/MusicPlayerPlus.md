---
tags:
  - projects
  - music
  - commandline
---

## MusicPlayerPlus

MusicPlayerPlus is a character-based console and terminal window music player
- ***plus*** Beets media library management with preconfigured plugins
- ***plus*** Character-based spectrum visualizer `mppcava`
- ***plus*** Music Player Daemon and ALSA configuration management
- ***plus*** Mopidy Music Server with preconfigured extensions
- ***plus*** Navidrome Music Server/Streamer automated install/config/service
- ***plus*** Bliss acoustic analysis and song similarity database
- ***plus*** Essentia acoustic analysis and metadata extraction
- ***plus*** YAMS MPD Last.fm scrobbler running as a service
- ***plus*** Media fuzzy finder using `fzf`
- ***plus*** Album cover art download
- ***plus*** Bandcamp collections download
- ***plus*** Soundcloud favorites download
- ***plus*** Automated setup, import and organization, metadata, playlists, ...

## Table of contents

1. [Overview](#overview)
    1. [Requirements](#requirements)
    1. [MusicPlayerPlus Commands](#musicplayerplus-commands)
1. [Quickstart](#quickstart)
    1. [Quickstart summary](#quickstart-summary)
    1. [Full Tilt Boogie](#full-tilt-boogie)
1. [Installation](#installation)
    1. [Supported platforms](#supported-platforms)
    1. [Debian package installation](#debian-package-installation)
    1. [RPM Package installation](#rpm-package-installation)
    1. [Arch Package installation](#arch-package-installation)
1. [Post Installation Configuration](#post-installation-configuration)
    1. [Client Configuration (required)](#client-configuration-required)
    1. [MusicPlayerPlus Configuration File](#musicplayerplus-configuration-file)
    1. [MPD Music Directory Configuration](#mpd-music-directory-configuration)
    1. [Initializing the Beets media library management system](#initializing-the-beets-media-library-management-system)
    1. [Additional metadata analysis and retrieval](#additional-metadata-analysis-and-retrieval)
        1. [Acoustic analysis with Blissify](#acoustic-analysis-with-blissify)
        1. [Acoustic analysis with Essentia](#acoustic-analysis-with-essentia)
        1. [Acoustic retrieval with AcousticBrainz](#acoustic-retrieval-with-acousticbrainz)
    1. [Activating the YAMS scrobbler for Last.fm](#activating-the-yams-scrobbler-for-lastfm)
    1. [MPD Audio Output Configuration](#mpd-audio-output-configuration)
    1. [Fuzzy Finder Configuration](#fuzzy-finder-configuration)
    1. [Start MPD](#start-mpd)
    1. [System verification checks](#system-verification-checks)
    1. [Initialize Music Database](#initialize-music-database)
    1. [Installing Mopidy](#installing-mopidy)
    1. [Installing Navidrome](#installing-navidrome)
        1. [Navidrome clients](#navidrome-clients)
    1. [Terminal Emulator Support](#terminal-emulator-support)
1. [MusicPlayerPlus Services and Clients](#musicplayerplus-services-and-clients)
    1. [Services](#services)
    1. [Which services should be installed and activated](#which-services-should-be-installed-and-activated)
    1. [Clients](#clients)
1. [Documentation](#documentation)
    1. [README for MusicPlayerPlus configuration](#readme-for-musicplayerplus-configuration)
    1. [README for mpcplus MPD client](#readme-for-mpcplus-mpd-client)
    1. [README for tmuxp configs](#readme-for-tmuxp-configs)
    1. [Man Pages](#man-pages)
    1. [Usage](#usage)
    1. [Example client invocations](#example-client-invocations)
    1. [Adding Album Cover Art](#adding-album-cover-art)
    1. [Custom key bindings](#custom-key-bindings)
    1. [Tmux session exit issues](#tmux-session-exit-issues)
1. [Removal](#removal)
1. [Troubleshooting](#troubleshooting)
    1. [Known issues](#known-issues)
1. [Infrared remote control of MPD](#infrared-remote-control-of-mpd)
1. [Screenshots](#screenshots)
1. [Videos](#videos)
1. [Building MusicPlayerPlus from source](#building-musicplayerplus-from-source)
1. [Contributing](#contributing)
    1. [Testing and Issue Reporting](#testing-and-Issue-Reporting)
    1. [Sponsor MusicPlayerPlus](#sponsor-musicplayerplus)
    1. [Contribute to Development](#contribute-to-development)
1. [See also](#see-also)

## Overview

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

The MusicPlayerPlus project provides integration and extension of several audio
packages designed to stream and play music. MusicPlayerPlus interacts with the
Music Player Daemon (MPD). Outputs from the MPD streaming audio server are used
as MusicPlayerPlus inputs for playback and visualization. MusicPlayerPlus
components are used to manage and control MPD and ALSA configuration.

MusicPlayerPlus integrations and extensions are primarily aimed at the
character-based terminal user. They enable an easy to use seamlessly
integrated control of audio streaming, playing, music library management,
and visualization in a lightweight character-based environment.

Audio streaming is provided by the Music Player Daemon (MPD).
At the core of MusicPlayerPlus is the `mpplus` command which acts as
a front-end for a variety of terminal and/or `tmux` sessions.

The `mpplus` command can be used to invoke:

* The lightweight character-based MPD client, `mpcplus`
* One or more terminal emulators running an MPD client and visualizer
* A tmux session using the tmux session manager `tmuxp`
* A spectrum visualizer
* A download of album cover art for every album in a music library
* Conversion of all WAV/M4A format media in a music library to MP3 format media
* An import of a music library to the Beets media library manager
* A download of lyrics for all songs in the music library without lyrics
* Analysis and retrieval of audio-based information for media matching a query
* YAMS MPD Last.fm scrobbler activation
* Any MPD client the user wishes to run
* One of several asciimatics animations optionally accompanied by audio
* A fuzzy listing and searching of the audio library using `fzf`

**[Note:]** Typical use of `mpplus` as a music player and spectrum visualizer
will invoke a `tmux` session to display the MPD client, spectrum visualizer, and
album cover art all in a single terminal window. MusicPlayerPlus configures
`tmux` with a custom key binding to exit tmux sessions. To exit an `mpplus`
tmux session, the `Alt-x` key binding can be used.

Integration is provided for:

* [mpd](https://www.musicpd.org/), the Music Player Daemon
* [mpcplus](https://github.com/doctorfree/mpcplus/README.md), character-based MPD client
* [beets](https://beets.io/), media library management system
* [essentia](https://github.com/doctorfree/mpplus-essentia/README.md), acoustic metadata analysis and extraction
* [mopidy](https://mopidy.com/), music server with cool extensions
* [navidrome](https://www.navidrome.org/), self-hosted music server and streamer
* [yams](https://github.com/Berulacks/yams/), MPD scrobbler for Last.fm
* [cava](https://github.com/karlstav/cava), an audio spectrum visualizer
* [mplayer](http://mplayerhq.hu/design7/info.html), a media player
* [fzf](https://github.com/junegunn/fzf), interactive fuzzy finder
* [asciimatics](https://github.com/peterbrittain/asciimatics) - automatically display a variety of character-based animation effects
* [asciinema](https://asciinema.org/) - automatically create ascii character-based video clips
* [tmux](https://github.com/tmux/tmux/wiki), a terminal multiplexer
* [tmuxp](https://github.com/tmux-python/tmuxp), a tmux session manager
* Enhanced key bindings for extended control of terminal windows and tmux sessions
* Several terminal emulators
    * kitty (the default MusicPlayerPlus terminal emulator)
    * cool-retro-term
    * gnome-terminal
    * tilix

The goal of MusicPlayerPlus is to provide the user with a sophisticated set
of complex music library tools that can be integrated and managed in a fairly
simple to understand fashion. Also, to make some cool looking powerful stuff
happen from the command-line in a character-based environment.

### Requirements

MusicPlayerPlus is compiled and packaged for installation on:

- Arch Linux (x86_64)
- CentOS Linux (x86_64)
- Fedora Linux (x86_64)
- Raspberry Pi OS (armhf)
- Ubuntu Linux (amd64)

Installation and initialization require admistrative privilege. The `mppinit`
command, executed after installing MusicPlayerPlus, installs several packages
and therefore requires access to the Internet along with administrative
privilege (e.g. `sudo` privilege).

Memory and storage requirements depend upon the size of the music library.

With a moderate sized music library, the Music Player Daemon can exceed a
2GB memory capacity. Therefore, 4GB or more of memory is recommended.

Storage should be sized to adequately host what will likely be a growing
music library. Plan ahead and leave your library room to grow. A few hundred
Gigabytes of storage might suffice for some music libraries but a Terabyte
or more will provide room to grow. Testing is performed on systems with
4GB RAM and 2TB storage using a 600GB music library.

Essentia metadata extraction, Blissify similarity analysis, and transcoding
all consume significant CPU resources. Testing has been performed on systems
with the following CPU resources:

- 8 x Intel(R) Core(TM) i7-7700K CPU @ 4.20GHz
- 2 x Intel(R) Celeron(R) CPU G1840 @ 2.80GHz
- 4 x ARMv7 Processor rev 3 (v7l)

All of these processors were able to handle significant loads. However,
import, metadata extraction, and transcoding are all much quicker on the
8 x Intel(R) Core(TM) i7-7700K CPU @ 4.20GHz system. Although not necessary,
these infrequent operations consume much less time on a more powerful CPU.

### MusicPlayerPlus Commands

MusicPlayerPlus adds the following commands to your system:

* **mpplus** : Primary user interface, invokes an MPD client, spectrum visualizer, and more
* **mpcplus** : Featureful NCurses MPD client, compiled with spectrum visualizer
* **mppinit** : One-time initializaton of a user's mpcplus configuration
* **mppcover** : Display album cover art for currently playing song
* **mppdl** : Downloads audio tracks from Bandcamp, Soundcloud, or a URL
* **mpcplus-tmux** : Runs mpcplus, a visualizer, and displays album art in a tmux session
* **mppsplash-tmux** : Runs mppsplash, a visualizer, in a tmux session
* **mppsplash** : Fun ascii art screens using ASCIImatics animations. Ascii art commands:
    * **mppjulia** : ASCIImatics animated zoom on a Julia Set
    * **mppplasma** : ASCIImatics animated plasma graphic
    * **mpprocks** : ASCIImatics animated MusicPlayerPlus splash screen
* **raise_cava** : Raises the mppcava spectrum visualizer window
* **set_term_trans** : Sets an xfce4-terminal window's transparency level
* **fzmp** : Browse, search, and manage MPD library using `fzf` fuzzy finder and `mpc` MPD client
* **artist_to_albumartist** : Copies the Artist tag to the AlbumArtist tag
* **create_playlist** : Create a new playlist using a Beets query
* **listyt** : List YouTube video titles and urls
* **bliss-analyze** : Acoustic analysis of audio files
* **blissify** : Create MPD playlists using song similarity
* **essentia_streaming_extractor_music** : Analyze and extract acoustic characteristics
* **mpd-configure** : Create an MPD configuration file optimized for bit perfect playback
* **mpd-monitor** : Display info on currently playing MPD song

The `bliss-analyze` and `blissify` commands are currently not available on
Raspberry Pi installations due to lack of support for that architecture in
the `ffmpeg` library.

**[Note:]** MusicPlayerPlus functions as a front-end and management system for
any MPD/Mopidy/Navidrome client. The default MPD client is `mpcplus` but any
MPD client can be configured by setting `MPD_CLIENT` in `~/.config/mpprc`.
While `mpcplus` is the recommended MPD client, `ncmpcpp` is also supported
with some integration for visualizer data source management. Other MPD clients
available for use with MusicPlayerPlus include ncmpc, pms, vimpc, pimpd2,
nncmpp, mmtc, and mpq.

Additional detail and info can be found in the
[MusicPlayerPlus Wiki](https://github.com/doctorfree/MusicPlayerPlus/wiki).

## Quickstart

### Required setup

* Create a music library if you do not already have one
    * Default MusicPlayerPlus location for the music library is `$HOME/Music`
    * Recommended structure of the music library is `artist/album/songs`
* Install the latest Arch, Debian, or RPM format installation package from the [MusicPlayerPlus Releases](https://github.com/doctorfree/MusicPlayerPlus/releases) page
* Run the `mppinit` command as your normal user
    * Searches `$HOME/Music` and `$HOME/music` for music library location
    * The music library location can be specified with `mppinit -l /path/to/library`

### Optional additional setup steps

For many installations, installing the MusicPlayerPlus package and initializing
the user configuration with the `mppinit` command is all that need be done.

Some common additional setup steps that can be performed include:

- Configuring the music library location
- Download albums in your Bandcamp collections
- Download favorites in your Soundcloud account
- Converting WAV/M4A format media files to MP3 format
- Importing a music library into the Beets library management system
- Downloading album cover art
- Downloading additional lyrics
- Activation of YAMS scrobbler for Last.fm
- Analysis and retrieval of audio-based information for media matching a query

Configure the music library location by editing `~/.config/mpprc` and setting
`MUSIC_DIR` to your music library location (default setting is `~/Music`).
Optionally configure any additional settings in `~/.config/mpprc` such as
your preferred terminal emulator, Bandcamp username, Soundcloud slug, or
more. Any changes to `~/.config/mpprc` must be followed by running the command
`mppinit sync`.

**[Important Note:]** MusicPlayerPlus integrates several services, each of
which has its own configuration for the location of the music library. Because
of this, MusicPlayerPlus provides its own configuration file
`~/.config/mpprc`. The `MUSIC_DIR` setting in that config file is used as the
source of truth for the location of the music library. In order to keep all
of the services in sync with respect to the music library location, set the
location in `~/.config/mpprc` and run the command `mppinit sync`.
If the music library is moved to a new location, repeat this procedure.

Download albums in your Bandcamp collections with `mppinit bandcamp`.

Download favorites in your Soundcloud account with `mppinit soundcloud`.

#### Two step post-initialization setup

The following optional post-initialization steps can be performed individually
as described below or they can be performed in two steps using `mppinit`.

**Step 1**, import the music library into Beets:

```
mppinit import
```

The `mppinit import` command converts any WAV format media to MP3 format
and imports the music library into the Beets media library management system.

**[Note:]** A Beets import can take hours for a large music library.
A test import using a music library over 500GB in size, with nearly
4000 artists, 3000 albums, and over 30,000 tracks consumed nearly 12 hours.
Import times will vary from system to system and library to library
depending on several factors. The above test may provide a ballpark idea
of the length of time a Beets library import might take.

When the import is complete

**Step 2**, retrieve additional metadata:

```
mppinit metadata
```

The `mppinit metadata` command identifies and deletes duplicate tracks,
retrieves album genres from Last.fm, downloads album cover art, and
(optionally) analyzes and retrieves metadata for all songs in the music library.

**[Note:]** A Beets metadata retrieval can take hours for a large music library.
The MusicPlayerPlus default Beets configuration uses `ffmpeg` to compute
checksums for every track in the library to find duplicates.

An optional audio analysis can be performed during metadata retrieval.
MusicPlayerPlus provides several optional methods for acoustic analysis.
The method used for acoustic analysis and retrieval can be specified
on the command line:

- AcousticBrainz metadata retrieval (deprecated)
    - `mppinit -a metadata`
- Blissify acoustic analysis of the MPD music library (the default)
    - `mppinit -b metadata`
- Essentia acoustic analysis and Beets metadata retrieval (long)
    - `mppinit -e metadata`

If none of the `-a, -b, or -e` options are specified then acoustic
analysis, extraction, and retrieval is performed by Essentia.

The AcousticBrainz service is the fastest method but is being retired in
2023, the service is no longer being updated, and it is often inaccurate.

The Essentia acoustic analysis is the most thorough, adds acoustic
metadata to the Beets library management system, and provides the greatest
flexibility but at a cost of possibly days of analysis and extraction time.
Metadata analysis and extraction with Essentia is the default behavior.

The Blissify analysis creates a similarity database of all songs in the music
library. This can be used to automate the creation of playlists and other
actions. The drawback of using Blissify is it does not add acoustic metadata
to the Beets library so the results of a Blissify analysis are only available
to Blissify and not Beets.

**[Note:]** Acoustic analysis with `blissify` is currently not available on
Raspberry Pi installations due to lack of support for that architecture in
the `ffmpeg` library.

It is sometimes desirable to augment one acoustic analysis with another.
For example, the AcousticBrainz service seems to think a lot of songs
have 0 beets per minute and tags them erroneously. After retrieving
metadata using AcousticBrainz, list the songs that have a bpm value of 0:

```
beet list bpm:0
```

These songs can get an accurate setting for bpm and other audio parameters
by following the `mppinit -a metadata` command with `mpplus -X bpm:0`.

#### Individual commands post-initialization setup

Download albums in your Bandcamp collections with `mppinit bandcamp`.

Download favorites in your Soundcloud account with `mppinit soundcloud`.

Convert WAV or M4A format media files in your library to MP3 format files with
the command `mpplus -F` or `mpplus -G`. Conversion from WAV to MP3 allows these
files to be imported into the Beets media library management system. Conversion
from M4A (Apple ALAC) to MP3 allows these files to be streamed and played in all
browsers supporting HTML5 audio (not necessary with Navidrome streaming).

If you wish to manage your music library with Beets, import the music library
with the command `mpplus -I`.

Album cover art can be downloaded with the command `mpplus -D art`.

Bandcamp collections can be downloaded with the command `mpplus -D bandcamp`.

Soundcloud favorites can be downloaded with the command `mpplus -D soundcloud`.

Download additional lyrics with the command `mpplus -L`.

Activate the YAMS scrobbler for Last.fm with the command `mpplus -Y`.

Analysis and retrieval of audio-based information can be performed with
the command `mpplus -X 'query'` where 'query' is a Beets library query.
The special query term 'all' indicates the entire music library, i.e.
`mpplus -X all`. Alternatively, query the AcousticBrainz service with
`mpplus -x all` or create a "song similarity" database using Blissify
with `mpplus -B`.

These common additional setup steps and more are covered in greater
detail in the [MusicPlayerPlus Beets README](../audio/beets.md) and the
[Post Installation Configuration](#post-installation-configuration)
section below.

### Quickstart summary

To summarize, a MusicPlayer quickstart can be accomplished by:

* Install the latest Arch, Debian, or RPM format installation package
* Run `mppinit` or `mppinit -l /path/to/library` as your normal user
* If the music library location was not properly detected:
    * Configure `MUSIC_DIR` by editing `~/.config/mpprc`
    * Run the command `mppinit sync`
* Optionally:
    * Modify user-specific settings in `~/.config/mpprc` and run `mppinit sync`
    * Download albums in your Bandcamp collections with `mppinit bandcamp`
    * Download favorites in your Soundcloud account with `mppinit soundcloud`
    * Perform these steps with the command `mppinit import`
        * Convert WAV format files to MP3 format with the command `mpplus -F`
        * Import your music library into Beets with the command `mpplus -I`
    * Perform these steps with the command `mppinit metadata`
        * Remove duplicate tracks with the command `beet duplicates -d`
        * Rename tracks left after duplicate removal with `beet move`
        * Download album cover art with the command `mpplus -D art`
        * Analyze and retrieve audio-based information with a command like:
		    * `mpplus -B` creates a "song similarity" database with Blissify
            * `mpplus -X all` analyze the entire Beets library with Essentia
            * `mpplus -X 'query'` where 'query' is a Beets library query
            * `mpplus -x all` query AcousticBrainz for the entire Beets library
    * Activate the YAMS scrobbler for Last.fm with the command `mpplus -Y`
    * Download additional lyrics with the command `mpplus -L`

### Full Tilt Boogie

The entire full tilt boogie initialization, for those with both Bandcamp
and Soundcloud accounts with songs and albums in a collection or liked,
and who wish to apply thorough, reliable, complete, and accurate metadata:

```
# Initialize MusicPlayerPlus, activate Music Player Daemon
# This is the only required setup step
mppinit

# For Bandcamp and Soundcloud users, a convenient way to download
mppinit bandcamp
mppinit soundcloud

# Beets library import (can take hours)
mppinit import

# Install, configure, and activate Mopidy music server
mppinit mopidy

# Install, configure, and activate Navidrome streaming music server
mppinit navidrome

# Perform analysis and extraction of acoustic metadata with Essentia
# This background process can take hours or even days for a large library
mppinit metadata
```

## Installation

MusicPlayerPlus v2.0.1 and later can be installed on Linux systems using
the Arch packaging format, the Debian packaging format, or the Red Hat
Package Manager (RPM).

### Supported platforms

MusicPlayerPlus has been tested successfully on the following platforms:

- **Arch Linux 2022.07.01**
    - `MusicPlayerPlus_<version>-<release>-x86_64.pkg.tar.zst`
- **Ubuntu Linux 20.04**
    - `MusicPlayerPlus_<version>-<release>.amd64.deb`
- **Fedora Linux 36**
    - `MusicPlayerPlus_<version>-<release>.x86_64.rpm`
- **CentOS Linux 8**
    - `MusicPlayerPlus_<version>-<release>.x86_64.rpm`
- **Raspbian Linux 11**
    - `MusicPlayerPlus_<version>-<release>.armhf.deb`

### Debian package installation

Many Linux distributions, most notably Ubuntu and its derivatives, use the
Debian packaging system.

To tell if a Linux system is Debian based it is usually sufficient to
check for the existence of the file `/etc/debian_version` and/or examine the
contents of the file `/etc/os-release`.

To install on a Debian based Linux system, download the latest Debian format
package from the
[MusicPlayerPlus Releases](https://github.com/doctorfree/MusicPlayerPlus/releases).

Install the MusicPlayerPlus package by executing the command

```console
sudo apt install ./MusicPlayerPlus_<version>-<release>.amd64.deb
```
or
```console
sudo dpkg -i ./MusicPlayerPlus_<version>-<release>.amd64.deb
```

or, on a Raspberry Pi:

```console
sudo apt install ./MusicPlayerPlus_<version>-<release>.armhf.deb
```
or
```console
sudo dpkg -i ./MusicPlayerPlus_<version>-<release>.armhf.deb
```

**[Note:]** In some cases you may see a warning message when installing the
Debian package. The message:

Repository is broken: musicplayerplus:amd64 (= <version-<release>) has no Size information

can safely be ignored. This is an issue with the Debian packaging system
and has no effect on the installation.

### RPM Package installation

Red Hat Linux, SUSE Linux, and their derivatives use the RPM packaging
format. RPM based Linux distributions include Fedora, AlmaLinux, CentOS,
openSUSE, OpenMandriva, Mandrake Linux, Red Hat Linux, and Oracle Linux.

To install on an RPM based Linux system, download the latest RPM format
package from the
[MusicPlayerPlus Releases](https://github.com/doctorfree/MusicPlayerPlus/releases).

Install the MusicPlayerPlus package by executing the command

```console
sudo yum localinstall ./MusicPlayerPlus_<version>-<release>.x86_64.rpm
```
or
```console
sudo rpm -i ./MusicPlayerPlus_<version>-<release>.x86_64.rpm
```

### Arch Package installation

Arch Linux, Manjaro, and other Arch Linux derivatives use the Pacman packaging
format. In addition to Arch Linux, Arch based Linux distributions include
ArchBang, Arch Linux, Artix Linux, ArchLabs, Asahi Linux, BlackArch,
Chakra Linux, EndeavourOS, Frugalware Linux, Garuda Linux,
Hyperbola GNU/Linux-libre, LinHES, Manjaro, Parabola GNU/Linux-libre,
SteamOS, and SystemRescue.

To install on an Arch based Linux system, download the latest Pacman format
package from the
[MusicPlayerPlus Releases](https://github.com/doctorfree/MusicPlayerPlus/releases).

Install the MusicPlayerPlus package by executing the command

```console
sudo pacman -U ./MusicPlayerPlus_<version>-<release>-x86_64.pkg.tar.zst
```

## Post Installation Configuration

**[Note:]** Extensive post-installation steps are covered here.
Minimal post-installation configuration required is the execution
of the command `mppinit`. If the MPD music library is located in
the default `$HOME/Music` directory then no further configuration
may be necessary. See the [Quickstart](#quickstart) section.

After installing MusicPlayerPlus there are several recommended
configuration steps. If not already configured, the MPD server
will need to know where to locate your music library. This can
be configured by editing the MusicPlayerPlus configuration file
`~/.config/mpprc` and running the command `mppinit sync`.

### Client Configuration (required)

Initialize the MusicPlayerPlus configuration by executing the command:

```
mppinit
```

Examine the generated configuration in `~/.config/mpprc` and make any desired changes.

The client configuration performed by `mppinit` includes the configuration
of an MPD user service. The configuration, files, and folders used by
this user level MPD service are stored in `~/.config/mpd/`. Examine the
generated MPD configuration file `~/.config/mpd/mpd.conf`.

### MusicPlayerPlus Configuration File

MusicPlayerPlus 2.0.1 release 3 and later provides the configuration file
`~/.config/mpprc` which serves as the primary source for MusicPlayerPlus
user configurable settings. This configuration file is the "source of truth"
for several settings including the music library location. Settings in
`mpprc` are propogated throughout several other component's configurations.

The settings in `mpprc` are *dynamic* and preserved across command invocations.
The dynamic nature of this configuration file means that options specified
on the `mpplus` command line or in the `mpplus` menu system are written back
out to `~/.config/mpprc` so the next invocation of `mpplus` will use the
previous invocation's options and settings as the default.

The default installed `mpprc` contains:

```
## MusicPlayerPlus runtime configuration
#
#  After modifying any of the following settings, run the command:
#    mppinit sync
#  as your normal MusicPlayerPlus user

## Music library location
#
MUSIC_DIR="~/Music"

## General settings
#
# To enable any of these, set to 1
# For example, to enable cover art display in tmux sessions set COVER_ART=1
#
# Play audio during asciimatics animations
AUDIO=1
# Display cover art in tmux sessions
COVER_ART=1
# Display mpcplus and mppcava in a tmux session
USE_TMUX=

## Terminal emulator / display mode
#
#  Can be one of: console, current, gnome, kitty, retro, simple, tilix
#  Where:
#    'console' will force a tmux session
#    'current' will force a tmux session in the current terminal window
#    'gnome' will use the gnome-terminal emulator if installed
#    'kitty' will use the kitty terminal emulator if installed
#    'retro' will use cool-retro-term if installed
#    'simple' will use the ST terminal emulator if installed
#    'tilix' will use the Tilix terminal emulator if installed
#  Default fallback if none specified or not available is kitty
#
#  Uncomment the preferred mode
#MPP_MODE=console
#MPP_MODE=current
#MPP_MODE=gnome
#MPP_MODE=retro
#MPP_MODE=simple
#MPP_MODE=tilix
MPP_MODE=kitty

## Service access
#
# The Bandcamp username can be found by visiting Bandcamp 'Settings' -> 'Fan'
# If you do not have a Bandcamp account, leave blank
BANDCAMP_USER=

# Your Last.fm username, api key, and api secret
# If you do not have a Last.fm account, leave blank
LASTFM_USER=
LASTFM_APIKEY=
LASTFM_SECRET=

# The Soundcloud user slug can be found by logging in to Soundcloud
# click on the username at top right then 'Profile'. The user slug
# is the last component of the URL when viewing your Soundcloud Profile.
# If you do not have a Soundcloud account, leave blank
SOUNDCLOUD_SLUG=

# Your Spotify client id and client secret
# If you do not have a Spotify account, leave blank
SPOTIFY_CLIENT=
SPOTIFY_SECRET=

# Your YouTube api key
# If you do not have a YouTube account, leave blank
YOUTUBE_APIKEY=
```

After `mppinit` completes the MusicPlayerPlus initialization, edit the
`~/.config/mpprc` configuration file and run `mppinit sync`.

### MPD Music Directory Configuration

**[Note:]** MusicPlayerPlus version 1.0.3 release 1 and later perform
an automated MPD user configuration and systemd service activation.
This is performed by the `mppinit` command. MusicPlayerPlus 1.0.3r1
and later installations need not perform the following manual procedures
but users may wish to review the automated MPD configuration and alter
the default MPD music directory location.

The default MPD and `mpcplus` music directory is set to:

`$HOME/Music`

If your media library resides in another location then perform the following
steps and run `mppinit sync`:

* Edit `$HOME/.config/mpprc` and set the `MUSIC_DIR` entry to the location of your music library (e.g. `vi ~/.config/mpprc`)
* Run the `mppinit sync` command

For example, to set the MPD music directory to the `/u/audio/music` directory,
edit `$HOME/.config/mpprc` and change the *MUSIC_DIR* setting:

```
MUSIC_DIR="/u/audio/music"
```

The *MUSIC_DIR* location must be writeable by your user.

Any time the MPD music directory is manually modified, run `mppinit sync`.

### Initializing the Beets media library management system

**[Note:]** Beets is NOT the now defunct music service purchased by Apple.
It is an open source media library management system.

MusicPlayerPlus includes the Beets media library management system
and preconfigured settings to allow easy integration with MPD and `mpcplus`.
Beets is an application that catalogs your music collection, automatically
improving its metadata. It then provides a suite of tools for manipulating
and accessing your music. Beets includes an extensive set of plugins that
can be used to enhance and extend the functionality of the media library
management Beets provides. Many Beets plugins are installed and configured
automatically by MusicPlayerPlus.

To get started using the Beets media library management system, it is
necessary to import your music library into the Beets database. This process
catalogs your music collection and improves its metadata. The default
Beets configuration provided by MusicPlayerPlus moves and tags files in the
music library during this process. It adds music library data to the Beets
database. To import your music library into Beets, issue the following command:

```
mppinit import
```

or to skip WAV format media conversion and just perform the Beets import:

```
mpplus -I
```

**[Note:]** If additional songs or albums are added to the music library
after the initial Beets import is performed, simply rerun `mppinit import`
or `beet import /path/to/new/items` to import any new library items.
To remove duplicates and retrieve metadata for the newly imported items,
run `mppinit metadata`.

After importing the music library into Beets, try playing something with:

```
beet play QUERY
```

Where 'QUERY' is a valid
[Beets query](https://beets.readthedocs.io/en/stable/reference/query.html).
This can be a simple string like
"blue" or "love" or a more complicated expression as described in the
Beets query documentation. The Beets `play` plugin should match the
query string to songs in your music library, add those songs to the
MPD queue, and play them. Use `beet ls QUERY` to see what would be played.

**[Note:]** MusicPlayerPlus has configured the Beets play plugin
to use the command `/usr/share/musicplayerplus/scripts/mpcplay.sh`
to play media with this plugin. This script clears the MPD queue,
adds any songs matching the query to the queue, and plays the MPD queue.
In addition, two arguments are supported: `--shuffle` and `--debug`.
These additional arguments are passed using the `--args` feature.
For example, to play all media matching the string "velvet" and shuffle
the order of play, issue the command `beet play --args --shuffle velvet`.

Example usage of the `beet play` command:

* `beet play velvet`
* `beet play playlist:1970s`
* `beet play --args --shuffle playlist:1990s`
* `beet play --args "--debug --shuffle" green eyes`

For instructions on Beets media library setup and use see the
[MusicPlayerPlus Beets README](../audio/beets.md).

Learn more about the Beets media library management system at
https://beets.io/

### Additional metadata analysis and retrieval

MusicPlayerPlus includes three methods for augmenting music library
metadata through acoustic analysis. These three methods are:

- AcousticBrainz metadata retrieval (deprecated)
    - initialized with `mppinit -a metadata`
- Blissify acoustic analysis of the MPD music library
    - initialized with `mppinit -b metadata`
- Essentia acoustic analysis and Beets metadata retrieval
    - initialized with `mppinit -e metadata`

#### Acoustic analysis with Blissify

Acoustic analysis with Blissify does not require a prior Beets import.
The Blissify acoustic analysis creates a song similarity database for
all the songs in the MPD music library. Initialize the Blissify database
with the command `blissify update <mpd music directory>`. For example,
assuming the default MPD music directory:

```
blissify update ~/Music
```

Blissify database initialization would have been automatically performed
during setup if metadata initialization were done with:

```
mppinit -b metadata
```

After initialization of the Blissify database, the `blissify` command can
be used to create an MPD playlist based on song similarities. For example,
to make a 30 song playlist that queues the closest song to the currently
playing song, then the closest song to the second song, etc, effectively
making a "path" through the songs, execute the command:

```
blissify playlist --seed-song 30
```

To save the current MPD playlist (queue), execute the command:

```
mpc save <playlist-name>
```

Note that the acoustic analysis and database creation performed by
Blissify does not update the Beets library database. In order to add
this additional acoustic metadata to the Beets library it is necessary
to perform an acoustic analysis with Essentia or acoustic metadata
retrieval with AcousticBrainz, both described in the next sections.

#### Acoustic analysis with Essentia

After completing the Beets music library import with either `mppinit import`
or `mpplus -I`, additional Beets metadata can be retrieved with the command:

```
mppinit -e metadata
```

This will identify and delete duplicate tracks, retrieve album genres,
download album cover art, and optionally analyze and retrieve metadata
for all songs in the music library using the
[Essentia extractor](https://essentia.upf.edu/index.html) and
[Essentia trained models](https://essentia.upf.edu/models.html).

MusicPlayerPlus `mppinit -e metadata` uses Essentia for extracting acoustic
characteristics of music, including low-level spectral information, rhythm,
keys, scales, and much more, and automatic annotation by genres, moods, and
instrumentation.

This is the same sort of thing that
[AcousticBrainz](https://acousticbrainz.org/) does but the AcousticBrainz
project is no longer collecting data and will be withdrawn in 2023.
MusicPlayerPlus provides the same functionality using pre-compiled and
packaged Essentia binaries and models.

However, the process of analyzing, extracting, and retrieving metadata
can be time consuming for a large music library. The `mppinit -e metadata`
command performs several metadata retrieval steps in a non-interactive
manner and in the background so it can be left unattended if desired.

#### Acoustic retrieval with AcousticBrainz

While it still exists the AcousticBrainz service can be queried to provide
a relatively quick way to update the Beets library with additional
acoustic metadata. The AcousticBrainz service has already analyzed the
acoustic characteristics of songs in the MusicBrainz catalog. To retrieve
this metadata for songs in your music library, after Beets import is complete,
run the command `mppinit -a metadata`. Or, at any time after Beets import
run the command `beet acousticbrainz`. The AcousticBrainz service is no longer
updated and will be retired in 2023.

The individual metadata retrieval steps performed automatically by
`mppinit [-a|-b|-e] metadata` can be performed manually using the instructions in
the [MusicPlayerPlus Beets README](../audio/beets.md).

### Activating the YAMS scrobbler for Last.fm

YAMS is an acronym for "Yet Another MPD Scrobbler".
When YAMS is configured and running, any songs, artists, or albums
played through MPD get "scrobbled" to [Last.fm](https://www.last.fm).
This enables a tracking of your listening patterns and habits,
creating a fairly extensive set of statistics viewable on Last.fm.

Features:

- Authenticate with the new Last.fm Scrobbling API v2.0 - without the need to input/store your username/password locally.
- Update your profile's "Now Playing" track via Last.fm's "Now Playing" API
- Save failed scrobbles to a disk and upload them at a later date.
- Timing configuration (e.g. scrobble percentage, real world timing values for scrobbling, etc.).
- Prevent accidental duplicate scrobbles on rewind/playback restart/etc.
- Automatic daemonization and config file generation.

In order to activate the YAMS scrobbler you will need an account with Last.fm.
Free accounts with Last.fm include many of the service features and can
provide extensive listening history statistics. If you do not wish to
use Last.fm to analyze MPD track plays then this optional setup step
can be ignored and no action is required as MusicPlayerPlus disables
YAMS by default. Disable a previously activated YAMS service with the
command `mpplus -y`.

Activate the YAMS scrobbler for Last.fm with the command:

```
mpplus -Y
```

The activation process must be run in a terminal window and will provide
you with a URL. Copy the URL and navigate to it using a web browser.
This will take you to Last.fm to authenticate if not already logged in
and authorize YAMS access. Once access is authorized there is no need
to authenticate for future Last.fm access with YAMS. There is also no
need to manually run the `yams` command as a user service is activated
to run it automatically. Basically, nothing else to do, just play music
and it will be scrobbled by YAMS.

YAMS creates a configuration file `$HOME/.config/yams/yams.yml`.

#### Using YAMScrobbler with Libre.fm

YAMS works fine with Libre.fm, a Free Software replacement for Last.fm.
If you prefer to use Libre.fm rather than Last.fm, do the following:

- Set the `base_url` config variable to `https://libre.fm/2.0/` in `$HOME/.config/yams/yams.yml` (don't forget the trailing slash!)
- Delete any leftover `.lastfm_session` files
- Authenticate like you normally would with Last.fm, however replace `last.fm` with `libre.fm` in the authorization URL printed out by YAMS

### MPD Audio Output Configuration

Adjust the `audio_output` settings in `~/.config/mpd/mpd.conf`.
MPD must have at least one `audio_output` configured and in order
to use the spectrum visualizer as configured by default it is necessary
to configure a second `audio_output` in MPD.

The default MPD `audio_output` setting is `PulseAudio`. To modify the MPD audio
output, uncomment one of `ALSA`, `PulseAudio`, or `PipeWire` and restart MPD.

A FIFO `audio_output` is used as a data source for the spectrum visualizer.
To configure this output, add the following to `~/.config/mpd/mpd.conf`:

```
audio_output {
    type            "fifo"
    name            "Visualizer feed"
    path            "~/.config/mpd/mpd.fifo"
    format          "44100:16:2"
}
```

An example ALSA `audio_output` configuration in `~/.config/mpd/mpd.conf`:

```
audio_output {
	type		"alsa"
	name		"ALSA"
    buffer_time "50000"   # (50ms); default is 500000 microseconds (0.5s)
#	device		"hw:0,0"	# optional
#	mixer_type      "hardware"      # optional
#	mixer_device	"default"	# optional
#	mixer_control	"PCM"		# optional
#	mixer_index	"0"		# optional
}
```

Or, to use PulseAudio:

```
audio_output {  
    type  "pulse"  
    name  "pulse audio"
    device         "pulse" 
    mixer_type      "hardware" 
}  
```

Output with PipeWire can also be configured:

```
audio_output {
    type  "pipewire"
    name  "PipeWire Sound Server"
}
```

MPD is a powerful and flexible music player server with many configuration
options. Additional MPD configuration may be desired. See the
[MPD User's Manual](https://mpd.readthedocs.io/en/stable/user.html)

### Fuzzy Finder Configuration

The `fzmp` command lists, searches, and selects media from the MPD
library using the `fzf` fuzzy finder command line utility. A default
`fzmp` configuration file for each user is created when the `mppinit`
command is executed. The `fzmp` configuration file is located at:

```
~/.config/mpcplus/fzmp.conf
```

The initial default `fzmp` configuration should suffice for most use cases.
Some of the interactive key bindings may need to be modified if they are
already in use by other utilities. For example, the default key binding to
switch to playlist view is 'F1' but the `xfce4-terminal` command binds 'F1'
by default to its help window. In this case either the `fzmp` playlist view
key binding must be changed or the XFCE4 terminal help window shortcut must
be disabled.

To disable the XFCE4 terminal help window shortcut, in `xfce4-terminal` select:

*Edit -> Preferences -> Advanced*

Select the *Disable help window shortcut key (F1 by default)* and Close
the Preferences dialog. The XFCE4 terminal help window shortcut will no
longer be bound to 'F1' and no modification to the playlist view key binding
for `fzmp` would be necessary.

To modify the `fzmp` playlist view key binding, edit the `fzmp` configuration
file `~/.config/mpcplus/fzmp.conf` and add a line like the following:

```
playlist_view_key F6
```

This revised configuration would change the playlist view key binding from
'F1' to 'F6' and the XFCE4 terminal help window shortcut could remain enabled
and bound to 'F1'.

Several other `fzmp` bindings and options can be configured. See `man fzmp`
for details.

### Start MPD

**[Note:]** MusicPlayerPlus version 1.0.3 release 1 and later perform
an automated MPD user configuration and systemd service activation.
Initialization with `mppinit` for these installations should automatically
start the user MPD service. No further action should be required for
MusicPlayerPlus v1.0.3r1 or later installations.

Status of the MPD service can be checked with:

```
systemctl --user status mpd.service
```

Installation and initialization of MusicPlayerPlus prior to v1.0.3r1
will need to start mpd as a system-wide service by executing the commands:

`sudo systemctl start mpd`

If you want MPD to start automatically on subsequent reboots, run:

`sudo systemctl enable mpd`

Alternatively, if you want MPD to start automatically when a client
attempts to connect:

`sudo systemctl enable mpd.socket`

### System verification checks

Once the music directory has been set correctly, album art downloaded,
music library imported, and `mppinit sync` has completed initialization,
some system checks can optionally be performed.

* Verify the `mpd` service is running and if not then start it:
    * `systemctl --user is-active mpd.service`
    * `systemctl --user start mpd.service`
* Update the MPD client database:
    * `mpc update`
* Verify the `mpd` service is enabled and if not enable it
    * `systemctl --user is-enabled mpd.service`
    * `systemctl --user enable mpd.service`
* Play music with `mpplus`
    * See the [online mpcpluskeys cheat sheet](https://github.com/doctorfree/MusicPlayerPlus/wiki/mpcpluskeys.1) or `man mpcpluskeys` for help navigating the `mpplus` windows
    * See the [online mpplus man page](https://github.com/doctorfree/MusicPlayerPlus/wiki/mpplus.1) or `man mpplus` for different ways to invoke the `mpplus` command

### Initialize Music Database

**[Note:]** MusicPlayerPlus version 1.0.3 release 1 and later perform an
automated MPD music database initialization during execution of `mppinit`.

For versions of MusicPlayerPlus prior to v1.0.3r1, initialize the music
database with an MPD client and update the database. The `mpcplus` MPD
client can be used for this or the standard `mpc` MPD client can be used.
With `mpcplus`, launch the `mpcplus` MPD client, verify the client window
has focus, and type `u` to update the database. With `mpc` simply execute
the command `mpc update`.

If your music library is very large this process can take several minutes
to complete. Once the music database has been updated you should see the
songs, albums, and playlists in your music library appear in the client view.

### Installing Mopidy

To install, configure, and activate Mopidy issue the command `mppinit mopidy`.
After Mopidy initialization completes, open `http://<ip address>:6680/iris`.
After adding music to the local music library, run `mopidy local scan`.

**[Note:]** In order to use the Mopidy-Beets extension, perform a
`mppinit import` and optionally `mppinit metadata` prior to `mppinit mopidy`.

The default music server in MusicPlayerPlus is the Music Player Daemon (MPD).
An alternate music server, Mopidy, is supported and can perform the same
functions as MPD, is compatible with MPD clients, and can be extended to
offer many more features.

Activating Mopidy will first deactivate MPD. The MusicPlayerPlus Mopidy
activation runs as a user level system service. Configuration for Mopidy
and Mopidy extensions resides in `$HOME/.config/mopidy/`. The MusicPlayerPlus
activation of Mopidy auto-configures Mopidy and the installed extensions.

In addition to the
[bundled Mopidy extensions](https://docs.mopidy.com/en/latest/),
the `mppinit mopidy` command installs the following Mopidy extensions:

- **Mopidy-Beets**
    - Mopidy extension for playing music from Beets' web plugin
- **Mopidy-Iris**
    - A comprehensive and mobile-friendly client that presents your library and extensions in a user-friendly and intuitive interface. Built using React and Redux
    - Open `http://<ip address>:6680/iris`
- **Mopidy-Mobile**
    - Fully control a Mopidy music server from your mobile device
    - Android App available on [Google Play](https://play.google.com/store/apps/details?id=at.co.kemmer.mopidy_mobile)
    - Other devices open `http://IP_Address:6680` in a browser
- **Mopidy-Mpd**
    - Mopidy extension for controlling Mopidy from MPD clients
- **Mopidy-Podcast**
    - Mopidy extension for searching and browsing podcasts
- **Mopidy-Podcast-iTunes**
    - Mopidy extension for searching and browsing iTunes podcasts
- **Mopidy-TuneIn**
    - A backend for playing music from the TuneIn online radio service
- **Mopidy-Scrobbler**
    - Mopidy extension for scrobbling music to Last.fm
    - Requires Last.fm username/password added to `~/.config/mopidy/mopidy.conf`

Additional Mopidy extensions can be installed and configured. For example,
to stream Spotify with Mopidy, install and configure the Mopidy-Spotify
extension. Learn more at https://mopidy.com/ext/

To view the effective Mopidy configuration run the command `mopidy config`.
This will display the full Mopidy configuration with passwords masked out
so that you can safely share the output with others for debugging.

**[Note:]** The Mopidy MPD extension provides compatibility with MPD
clients but does not implement all MPD features. MPD is much more powerful
and flexible in terms of its configurable inputs and outputs. After
activating Mopidy some features may not work the same as they did with MPD.
For example, spectrum visualization may fail or player stats may not be
available. However, Mopidy offers many features unavailable with MPD.
It's a tradeoff.

To re-activate MPD and disable Mopidy, issue the command `mppinit mpd`.
Easily switch back and forth between MPD and Mopidy with `mppinit mpd`
and `mppinit mopidy`. Note that MusicPlayerPlus continues to use the
configured `MUSIC_DIR` as the master music library location.
To change the location of the music library, edit
`~/.config/mpprc`, set `MUSIC_DIR` to the new location,
and run `mppinit sync` to synchronize the music library location across
Beets, MPD, Mopidy, and downloaders.

### Installing Navidrome

The default music server in MusicPlayerPlus is the Music Player Daemon (MPD).
An alternate music server and streamer, Navidrome, is also supported.
To install, configure, and activate Navidrome issue the command:

```
mppinit navidrome
```

The MusicPlayerPlus Navidrome activation runs as a user level system service.
Configuration for Navidrome resides in `$HOME/.config/navidrome/navidrome.toml`.
The MusicPlayerPlus activation of Navidrome auto-configures, starts, and
enables the Navidrome service. The Navidrome log file can be found at
`$HOME/.config/navidrome/navidrome.log`.

After installing Navidrome, you need to create your first user. This will be
your admin user, a super user that can manage all aspects of Navidrome,
including the ability to manage other users. Browse to Navidrome’s homepage
at http://localhost:4533

Fill out the username and password you want to use, confirm the password and
click on the “Create Admin” button. You should now be able to browse and
listen to all your music.

**[Note:]** It usually take a couple of minutes for your music to start
appearing in Navidrome’s UI. Check the logs to see what is the scan progress.

**[Security Note:]** Navidrome comes with an embedded, full-featured HTTP
server but in order to provide additional security (e.g. SSL) Navidrome
should be run behind a reverse proxy like Nginx or Apache. MusicPlayerPlus
does not configure a reverse proxy for Navidrome. See the Navidrome network
configuration documentation at https://www.navidrome.org/docs/usage/security/
to get started securing Navidrome. To use the MusicPlayerPlus default
configuration of Navidrome, use `http://...` rather than `https://...`.

If all you want is a Navidrome streaming music server and you do not care
about Beets library management, additional downloads, or a Mopidy server
then setup can be accomplished with just `mppinit` followed by
`mppinit navidrome`.

#### Navidrome clients

The Navidrome self-hosted music service can stream your music to many devices.

MusicPlayerPlus tested and recommended free open source Navidrome clients:

- **iPhone/iPad**
    - [iSub](http://www.subsonic.org/pages/apps.jsp#isub)
- **Android**
    - [Dsub](http://www.subsonic.org/pages/apps.jsp#dsub)
- **Linux/MacOS/Windows**
    - [Sonixd](https://github.com/jeffvli/sonixd)

Character based terminal/console Navidrome clients:

- **Linux/Windows**
    - [Jellycli](https://github.com/tryffel/jellycli)
- **Linux**
    - [Stmp](https://github.com/wildeyedskies/stmp)

Navidrome clients are not installed by MusicPlayerPlus. Install Navidrome
clients using your device's app store or following the installation
instructions at the client link above.

If you do not have or wish to use a Navidrome client, then most modern
browsers are supported Navidrome clients. To use a browser as a Navidrome
web client, open the URL `http://ip-address:4533` where *ip-address* is
the IP address of the Navidrome server.

For a list of Airsonic compatible applications, see
https://airsonic.github.io/docs/apps/

For a list of Subsonic compatible clients, see
https://www.navidrome.org/docs/overview/#apps

[Sonixd](https://github.com/jeffvli/sonixd) is a cross-platform desktop
Subsonic client compatible with Navidrome. On Apple MacOS, install sonixd
with Homebrew:

```
brew install --cask sonixd
```

[Sublime](https://sublime-music.gitlab.io/sublime-music/index.html) is a
native Subsonic client compatible with Navidrome for the Linux Desktop.
See https://sublime-music.gitlab.io/sublime-music/index.html to install
Sublime on a variety of Linux distributions.

### Terminal Emulator Support

Supported terminal emulators in MusicPlayerPlus include `kitty`, `tilix`,
`gnome-terminal`, `st`, and `cool-retro-term`. Kitty is the default terminal
emulator used by MusicPlayerPlus except on Raspberry Pi OS where `st` is used
as the default.

**[Note:]** The [kitty terminal emulator](https://sw.kovidgoyal.net/kitty/)
is very cool. A default kitty theme is provided (the 'Music Player Plus' theme)
and should suffice for most users. An alternate kitty theme can be configured
using the kitty themes kitten. To use this kitten, run:

```
kitty +kitten themes
```

An alternate terminal emulator can be specified on the `mpplus` command line:

```
mpplus -c ... # indicates use the current terminal and a tmux session
mpplus -e ... # indicates use the simple terminal emulator (st)
mpplus -g ... # indicates use the gnome terminal emulator
mpplus -k ... # indicates use the kitty terminal emulator
mpplus -r ... # indicates use the cool-retro-term terminal emulator
mpplus -t ... # indicates use the tilix terminal emulator
```

If an alternate terminal emulator is not specified on the command line
then the default will be used unless console mode is detected. Console mode
is used when no DISPLAY can be opened (e.g. running on a console, running
over SSH without a display, running on a headless server). In console mode
MusicPlayerPlus utilizes `tmux` sessions to display the character-based music
player `mpcplus` and spectrum visualizer `mppcava`.

The `mppcava` spectrum visualizer looks better when the font used by the
terminal emulator in which it is running is a small sized font. Some
terminal emulators rely on a profile from which they draw much of
their configuration. Profiles are used in MusicPlayerPlus to provide
an enhanced visual presentation.

In order to use the Gnome, Simple, or Tilix terminal emulators they must be
installed manually (except on Raspberry Pi OS where the Simple terminal
emulator is installed if no supported terminal emulator is found).
If you wish to use the Gnome, Simple, or Tilix terminal emulators,
then use your system's package manager to install them prior to
initializing MusicPlayerPlus with the `mppinit` command. If either or both
of Gnome or Tilix terminal emulators are installed after MusicPlayerPlus
initialization with `mppinit` then run `mppinit profiles` after installing
gnome-terminal or tilix terminal emulator(s).

There are four terminal profiles in two terminal emulators used by
MusicPlayerPlus. The `gnome-terminal` emulator and the `tilix` terminal
emulator each have two custom profiles created during `mppinit` initialization.
These profiles are named "MusicPlayer" and "Visualizer".

The custom MusicPlayerPlus terminal profiles are used to provide font sizes
and background transparencies that enhance the visual appeal of both the
MusicPlayerPlus control window and the spectrum visualizer. 

To modify these terminal emulator profiles, launch the desired terminal
emulator and modify the desired profile in the Preferences dialog.

## MusicPlayerPlus Services and Clients

MusicPlayerPlus includes several services, some installed by default and
others optionally installed with the `mppinit` command post-installation.
Clients that can be used to access these services are also provided.

### Services

The following services are included with MusicPlayerPlus:

- **Music Player Daemon (MPD)**
    - Installed, configured, and activated by default
- **MPD Stats Service**
    - Installed, configured, and activated by default
- **Beets Web Plugin Service**
    - Installed, configured, and activated by default
- **Mopidy Music Server**
    - Installed, configured, and activated with `mppinit mopidy`
    - When activated, deactivates MPD, MPD Stats, and YAMS services
- **Navidrome Music Streaming Server**
    - Installed, configured, and activated with `mppinit navidrome`
- **YAMS Last.FM Scrobbler**
    - Installed, configured, and activated with `mppinit yams`

All of the MusicPlayerPlus services are user-level systemd services and can
be controlled by the MusicPlayerPlus user without the need for `root` privilege.
The `mpplus -i` interactive menu system includes menu entries for controlling
each of these services as well as a status report on them by selecting the
"Manage Music Services" from the Main Menu. Alternately, each service can
be controlled from the command line using `systemctl --user ...`. For example,
to stop the MPD Stats Service, run the command `systemctl --user stop mpdstats`.

### Which services should be installed and activated

Depending upon the use case and personal preference, a variety of combinations
of MusicPlayerPlus services can be activated. Mopidy with the Mopidy-MPD
extension conflicts with the MPD service. YAMS and MPD Stats only work with
MPD. Therefore, if Mopidy is activated the MPD, YAMS, and MPD Stats services
are automatically deactivated. Similarly, if the MPD service is reactivated,
the YAMS and MPD Stats services are reactivated and Mopidy deactivated.

Choose which service you prefer, MPD or Mopidy, and activate it with either
`mppinit mopidy` or `mppinit mpd` (after activating Mopidy then deciding to
reactivate MPD). Using these two commands, `mppinit mopidy` and `mppinit mpd`,
it is easy to switch between the two conflicting services.

The advantage of MPD is its stability, maturity, flexibility, power, and
extensive configuration options. However, it is difficult to enable streaming
with MPD. The advantage of Mopidy is its streaming capability and the variety
of useful extensions, many of which are installed by default with
`mppinit mopidy`.

An even better streaming solution is provided by Navidrome. Activating
Navidrome enables access to the music library from any desktop, phone,
tablet, or remote device with a browser. There are numerous Navidrome clients
available for all devices and platforms. Activating Navidrome does not conflict
with any of the other MusicPlayerPlus services so it can be streaming the
music library while MPD or Mopidy is serving up the same library locally.
Navidrome can optionally scrobble to Last.FM so if that option is enabled
then deactivate the YAMS service.

**[Summary]** MusicPlayerPlus provides several different selections of
services appropriate for a variety of use cases. All service configurations
require a prior MusicPlayerPlus initialization with `mppinit`. Some common
MusicPlayerPlus service configurations include:

- **Basic Music Player Daemon**
    - Configured automatically with `mppinit`
    - MPD enabled and active, all other services disabled
    - Use `mpplus`, `mpcplus`, `mpc`, etc to play music on local system
- **Music Player Daemon plus Beets**
    - Configured with `mppinit import`
    - MPD and Beets enabled and active, all other services disabled
    - Use `beet ...`, `mpplus`, `mpcplus`, `mpc`, to search, filter, play, ...
    - Enables the Beets web plugin at `http://<ip address>:8337`
- **Mopidy Music Server plus Beets**
    - Configured with `mppinit import`, and `mppinit mopidy`
    - Mopidy and Beets enabled and active, other services disabled
    - Use `beet ...`, `mpplus`, `mpcplus`, `mpc`, to search, filter, play, ...
    - Enables the Beets web plugin at `http://<ip address>:8337`
    - Enables the Mopidy web client at `http://<ip address>:6680`
- **Navidrome Streaming plus Mopidy Music Server plus Beets**
    - Configure with `mppinit import`, `mppinit mopidy`, `mppinit navidrome`
    - Navidrome, Mopidy and Beets enabled and active, other services disabled
    - Use `beet ...`, `mpplus`, `mpcplus`, `mpc`, to search, filter, play, ...
    - Enables the Beets web plugin at `http://<ip address>:8337`
    - Enables the Mopidy web client at `http://<ip address>:6680`
    - Enables the Navidrome web client at `http://<ip address>:4533`
    - Supports many clients available for all desktops, tablets, and phones
    - Run `mppinit import` after new `mppinit bandcamp|soundcloud` downloads
- **Navidrome Music Streaming Server without MPD/Mopidy/Beets**
    - Configure with `mppinit navidrome`
    - No need for `mppinit import|metadata|mopidy|yams`
    - Use `mpplus -i` menu system to stop and disable all other services
        - Select "Manage Music Services" from the Main Menu
        - If active, Stop and Disable MPD, Mopidy, and Beets
    - Navidrome enabled and active, other services disabled
    - Enables the Navidrome web client at `http://<ip address>:4533`
    - Supports many clients available for all desktops, tablets, and phones
    - No need for `mppinit import` after `mppinit bandcamp|soundcloud` downloads

### Clients

The following clients are included with MusicPlayerPlus:

- **mpplus MusicPlayerPlus front-end**
    - Installed by default, see `man mpplus`
    - Front-ends `mpcplus` MPD client and `mppcava` spectrum visualizer
    - Example: `mpplus`
- **mpcplus character-based feature-full MPD client**
    - Installed by default, see `man mpcplus`
    - Example: `mpcplus`
- **mpc command-line MPD client**
    - Installed by default, see `man mpc`
    - Examples: `mpc stop`, `mpc current`, `mpc play`
- **beet command-line interface to Beets**
    - Installed by default, see `man beet`
    - Examples: `beet play jethro tull`, `beet info -l aqualung`
- **Beets web client**
    - Installed by default
    - Open `http://<ip address>:8337`
- **Mopidy web client**
    - Installed, configured, and activated with `mppinit mopidy`
    - Open `http://<ip address>:6680`
- **Mopidy Iris web client**
    - Installed, configured, and activated with `mppinit mopidy`
    - Open `http://<ip address>:6680/iris`
- **Mopidy-Mobile**
    - Installed, configured, and activated with `mppinit mopidy`
    - Open `http://<ip address>:6680/mobile`
- **Navidrome web client**
    - Installed, configured, and activated with `mppinit navidrome`
    - Open `http://<ip address>:4533`

## Documentation

**[NEW:]** MusicPlayerPlus documentation is now available on [Read the Docs](https://musicplayerplus.readthedocs.io/en/latest/)

All MusicPlayerPlus commands have manual pages. Execute `man <command-name>`
to view the manual page for a command. The `mpplus` frontend is the primary
user interface for MusicPlayerPlus and the manual page for `mpplus` can be
viewed with the command `man mpplus`. Most commands also have
help/usage messages that can be viewed with the **-u** argument option,
e.g. `mpplus -u`.

### README for MusicPlayerPlus configuration
- [**config/README.md**](https://github.com/doctorfree/MusicPlayerPlus/blob/master/config/README.md) - Overview and details of the MusicPlayerPlus configuration

### README for mpcplus MPD client
- [**mpcplus/README.md**](https://github.com/doctorfree/mpcplus/README.md) - Introduction to the mpcplus MPD client

### README for tmuxp configs
- [**config/tmuxp/README.md**](https://github.com/doctorfree/MusicPlayerPlus/blob/master/config/tmuxp/README.md) - How to invoke the MusicPlayerPlus provided `tmuxp` session configurations

### Man Pages

- [**mpplus**](man/mpplus.1.md) : Primary MusicPlayerPlus user interface
- [**mppcava**](man/mppcava.1.md) : Audio Spectrum Visualizer
- [**mppjulia**](man/mppjulia.1.md) : asciimatics animation of a Julia Set
- [**mpprocks**](man/mpprocks.1.md) : asciimatics animation of MusicPlayerPlus intro
- [**mppplasma**](man/mppplasma.1.md) : asciimatics animation with Plasma effect
- [**mppinit**](man/mppinit.1.md) : MusicPlayerPlus initialization
- [**mppcover**](man/mppcover.1.md) : Displays album cover art for currently playing song
- [**mppdl**](man/mppdl.1.md) : Downloads audio tracks from Bandcamp, Soundcloud, or a URL
- [**mpcplus-tmux**](man/mpcplus-tmux.1.md) : MusicPlayerPlus in a tmux session
- [**mpcplus**](man/mpcplus.1.md) : MusicPlayerPlus MPD client
- [**mpcpluskeys**](man/mpcpluskeys.1.md) : Cheat sheet for `mpcplus` MPD client navigation
- [**mppsplash-tmux**](man/mppsplash-tmux.1.md) : MusicPlayerPlus asciimatics animations in a tmux session
- [**mppsplash**](man/mppsplash.1.md) : MusicPlayerPlus asciimatics animations
- [**mpd-configure**](man/mpd-configure.1.md) : MPD configuration generator
- [**mpd-monitor**](man/mpd-monitor.1.md) : Display info on currently playing MPD song
- [**beet**](man/beet.1.md) : Beets media library management command-line interface
- [**beetsconfig**](man/beetsconfig.5.md) : Beets media library management configuration
- [**bandcamp-dl**](man/bandcamp-dl.1.md) : Download Bandcamp collections
- [**blissify**](man/blissify.1.md) : create MPD playlists using song similarity database
- [**scdl**](man/scdl.1.md) : Download Soundcloud favorites
- [**fzmp**](man/fzmp.1.md) : List and search MPD media using fuzzy find
- [**artist_to_albumartist**](man/artist_to_albumartist.1.md) : Copies the Artist tag to the AlbumArtist tag
- [**listyt**](man/listyt.1.md) : List YouTube video titles and urls
- [**yt-dlp**](man/yt-dlp.1.md) : Download YouTube and other sites videos and audio
- [**create_playlist**](man/create_playlist.1.md) : Create playlists using Beets queries

### Usage

The primary MusicPlayerPlus user interface is the `mpplus` command.
The default action of the `mpplus` command is to open the `mpcplus`
MPD client and the `mppcava` spectrum visualizer. The command
`mpplus -i` displays a series of interactive menus from which most
of the MusicPlayerPlus tasks can be launched.

The `mpc` command provides a quick and easy command line interface
to control the Music Player Daemon playback. The `mpc` command has
many command line options, see `man mpc` for a full description.
To get started with simple MPD playback control using `mpc`:

**mpc toggle**
: start playback if stopped or paused, and pause playback if playing

**mpc stop**
: stop playback

**mpc next**
: move to next song in playlist

**mpc prev**
: move to previous song in playlist

**mpc volume +|- percent**
: increase or decrease volume by 'percent'

The `beet play [QUERY]` command can be used to specify a song or songs
to play where 'QUERY' is a Beets query matching songs in the music library.

The usage messages for `mppinit`, `mpplus`, `mpcplus`, and `mppcava`
provide a brief summary of the command line options.

The `mppinit` performs one-time initializations:

```
Usage: mppinit [-a] [-b] [-d] [-e] [-l music_dir] [-o] [-q] [-r] [-U] [-y] [-u] [bandcamp|import|kitty|metadata|mopidy|mpd|navidrome|soundcloud|sync|yams]
Where:
	'-a' use AcousticBrainz for acoustic audio analysis (deprecated)
	'-b' use Blissify for MPD acoustic audio analysis
	'-d' install latest Beets development branch rather than
		the latest stable release (for testing purposes)
	'-e' use Essentia for Beets acoustic audio analysis (default)
	'-l music_dir' specifies the location of the music library
	'-o' indicates overwrite any pre-existing configuration
	'-q' indicates quiet execution, no status messages
	'-r' indicates remove service
		supported service removals: mopidy navidrome
	'-U' indicates do not upgrade installed Python modules
	'-y' indicates answer 'yes' to all and proceed
	'-u' displays this usage message and exits

	'bandcamp' downloads all albums in your Bandcamp collections
	'import' performs a Beets music library import
	'kitty' installs the kitty terminal emulator
	'metadata' performs a library metadata update
	'mopidy' installs and configures Mopidy extensible music server
		Note: activating Mopidy deactivates MPD
	'mpd' activates the MPD music server and deactivates Mopidy
	'navidrome' installs and configures Navidrome music server
		Note: 'mppinit navidrome <version>' can be used to specify
		an alternate version of Navidrome to download and install
	'soundcloud' downloads all favorites in your Soundcloud account
	'sync' synchronizes MusicPlayerPlus configuration across configs
	'yams' activates the YAMS Last.fm scrobbler service

'mppinit' must be run as the MusicPlayerPlus user, not root.
'mppinit' must be run prior to 'mppinit sync', 'mppinit kitty',
	'mppinit metadata', 'mppinit bandcamp', 'mppinit mopidy',
	'mppinit navidrome', 'mppinit soundcloud', or 'mppinit import'
```

The `mpplus` command serves as a general user interface for all of the
MusicPlayerPlus capabilities:

```
Usage: mpplus [-A] [-a] [-b] [-B] [-c] [-C client] [-E] [-e] [-F] [-f]
	[-G] [-g] [-D art|bandcamp|soundcloud] [-d music_directory] [-h]
	[-H] [-I] [-i] [-jJ] [-k] [-K] [-L] [-m] [-n num] [-N]
	[-M alsaconf|enable|disable|restart|start|stop|status] [-p]
	[-P script] [-q] [-r] [-R] [-s song] [-S] [-t] [-T on|off] [-uU]
	[-v viz_comm] [-w|W] [-x query] [-X query] [-y] [-Y] [-z fzmpopt]
MPCplus/Visualizer options:
	-A indicates display album cover art (implies tmux session)
	-C 'client' indicates use 'client' MPD client rather than mpcplus
	-E indicates do not use gradient colors for spectrum visualizer
	-f indicates fullscreen display
	-h indicates half-height for visualizer window (with -f only)
	-H indicates disable use of extended window manager hints
	-P script specifies the ASCIImatics script to run in visualizer pane
	-q indicates quarter-height for visualizer window (with -f only)
	-c indicates use current terminal emulator / console mode
	-e indicates use simple terminal emulator
	-g indicates use gnome terminal emulator
	-k indicates use kitty terminal emulator
	-r indicates use retro terminal emulator
	-t indicates use tilix terminal emulator
	-U indicates use tmuxp to create tmux sessions
	-v 'viz_comm' indicates use visualizer 'viz_comm' rather than mppcava
ASCIImatics animation options:
	-a indicates play audio during ASCIImatics display
	-b indicates use backup audio during ASCIImatics display
	-j indicates use Julia Set scenes in ASCIImatics display
	-J indicates Julia Set with several runs using different parameters
	-m indicates use MusicPlayerPlus scenes in ASCIImatics display
	-n num specifies the number of times to cycle ASCIImatics scenes
	-N indicates use alternate comments in Plasma ASCIImatics scenes
	-p indicates use Plasma scenes in ASCIImatics display
	-s song specifies a song to accompany an ASCIImatics animation
		'song' can be the full pathname to an audio file or a
		relative pathname to an audio file in the MPD music library
		or $HOME/Music/
	-S indicates display ASCIImatics splash animation
General options:
	-B indicates analyze MPD music dir with Blissify and exit
	-D 'art' indicates download album cover art and exit
	-D 'bandcamp' indicates download Bandcamp songs and exit
	-D 'soundcloud' indicates download Soundcloud songs and exit
	-d 'music_directory' specifies the music directory to use for
		downloaded album cover art. Without this option -D will use
		the 'MUSIC_DIR' setting in '~/.config/mpprc'
	-F indicates convert WAV format files in the music library
		to MP3 format files and exit. A subsequent 'mpplus -I' import
		will be necessary to import these newly converted music files.
	-G indicates convert M4A format files in the music library
		to MP3 format files and exit. A subsequent 'mpplus -I' import
		will be necessary to import these newly converted music files.
	-I indicates import albums and songs from 'music_directory' to beets and exit
		In conjunction with '-I', the '-A' flag disables auto-tagging
	-i indicates start mpplus in interactive mode
	-K indicates kill MusicPlayerPlus tmux sessions and ASCIImatics scripts
	-L indicates download lyrics to the Beets library and exit
	-M 'action' can be used to control the Music Player Daemon (MPD)
	    or configure the ALSA sound system
		ALSA configuration will update the ALSA configuration in '/etc/asound.conf'
	-R indicates record tmux session with asciinema
		Asciinema is not installed by MusicPlayerPlus
		To record tmux sessions with asciinema, use your system's
		package manager to install it (e.g. apt install asciinema)
	-T 'on|off' specifies whether to use a tmux session
	-w indicates write metadata during beets import
	-W indicates do not write metadata during beets import
	-x 'query' uses AcousticBrainz to retrieve audio-based information
		for all music library media matching 'query'. A query
		of 'all' performs the retrieval on the entire music library.
	-X 'query' performs an analysis and retrieval, using Essentia,
		of audio-based information for all music library media
		matching 'query'. A query of 'all' performs the analysis
		and retrieval on the entire music library.
	-Y initializes the YAMS last.fm scrobbler service
	-y disables the YAMS last.fm scrobbler service
	-z fzmpopt specifies the fzmp option and invokes fzmp to
		list/search/select media in the MPD library.
		Valid values for fzmpopt are 'a', 'A', 'g', 'p', or 'P'
	-u displays this usage message and exits
```

The `mpcplus` command is an MPD client and acts as the primary
MusicPlayerPlus music player:

```
Usage: mpcplus [options]...
Options:
  -h [ --host ] HOST (=localhost)       connect to server at host
  -p [ --port ] PORT (=6600)            connect to server at port
  --current-song [=FORMAT(={{{(%l) }{{%a - }%t}}|{%f}})]
                                        print current song using given format 
                                        and exit
  -c [ --config ] PATH (=~/.config/mpcplus/config AND ~/.mpcplus/config)
                                        specify configuration file(s)
  --ignore-config-errors                ignore unknown and invalid options in 
                                        configuration files
  --test-lyrics-fetchers                check if lyrics fetchers work
  -b [ --bindings ] PATH (=~/.config/mpcplus/bindings AND ~/.mpcplus/bindings)
                                        specify bindings file(s)
  -s [ --screen ] SCREEN                specify the startup screen
  -S [ --slave-screen ] SCREEN          specify the startup slave screen
  -? [ --help ]                         show help message
  -v [ --version ]                      display version information
  -q [ --quiet ]                        suppress logs and excess output
```

The mpcplus MPD client has a customized set of key bindings that allow
quick and easy control of MPD, searches, lyrics display, client navigation,
and much more via the keyboard. View the
[**mpcpluskeys man page**](../audio/mpcpluskeys.1.md) with the command
`man mpcpluskeys`.

The `mppsplash` command can be used to display a variety of character
based animations optionally accompanied by audio:

```
Usage: mppsplash [-A] [-a] [-b] [-C] [-c num] [-d] [-jJ] [-m] [-p] [-s song] [-u]
Where:
	-A indicates use all effects
	-a indicates play audio during ASCIImatics display
	-b indicates use backup audio during ASCIImatics display
	-C indicates use alternate comments in Plasma effect
	-c num specifies the number of times to cycle
	-d indicates enable debug mode
	-j indicates use Julia Set effect
	-J indicates Julia Set with several runs using different parameters
	-m indicates use MusicPlayerPlus effect
	-p indicates use Plasma effect
	-s song specifies the audio file to play as accompaniment
		'song' can be the full pathname to an audio file or a relative
		pathname to an audio file in the MPD music library or
		$HOME/Music/
	-u displays this usage message and exits
```

The `mppcava` command is the MusicPlayerPlus custom character based
audio spectrum visualizer:

```
Usage : mppcava [options]
Visualize audio input in terminal. 

Options:
    -p          path to config file
    -v          print version

Keys:
        Up        Increase sensitivity
        Down      Decrease sensitivity
        Left      Decrease number of bars
        Right     Increase number of bars
        r         Reload config
        c         Reload colors only
        f         Cycle foreground color
        b         Cycle background color
        q         Quit

All options are specified in a config file. See `$HOME/.config/mppcava/config`
```

### Example client invocations
The `mpplus` command is intended to serve as the primary interface to invoke
the `mpcplus` MPD client and `mppcava` spectrum visualizer. The `mpplus` command
utilizes several different terminal emulators and can also be used to invoke
any specified MPD client. Some example invocations of `mpplus` follow.

Open the mpcplus client and spectrum visualizer in fullscreen mode:

`mpplus -f`

Open the mpcplus client and mppcava visualizer in fullscreen mode using the
tilix terminal emulator and displaying the visualizer using quarter-height:

`mpplus -f -q -t`

Open the cantata MPD graphical client and mppcava visualizer:

`mpplus -C cantata`

Open the mpcplus client in the cool-retro-term terminal and mppcava visualizer
in kitty:

`mpplus -r`

Browse, list, search, and select media in the MPD library using the
`fzf` fuzzy finder utility.

Search artist then filter by album using `fzf`:

`mpplus -z a`

Search all songs in the library using `fzf`:

`mpplus -z A`

Search the current playlist using `fzf`:

`mpplus -z p`

The mpcplus MPD client can be opened directly without using mpplus.
Similarly, the mppcava spectrum visualizer can be opened directly without mpplus.

`mpcplus` # In one terminal window

`mppcava` # In another terminal window

To test the mpcplus lyrics fetchers:

`mpcplus --test-lyrics-fetchers`

### Adding Album Cover Art

The `mpcplus` MPD client is a character-based application. As such, it is
difficult to display graphical images. However, this limitation can be
overcome using `tmux` and additional tools. In this way we can add album
cover art to MusicPlayerPlus when using the character-based `mpcplus` client.

See `Adding album art to MusicPlayerPlus` to get
started integrating album art in MusicPlayerPlus.

An album cover art downloader is included in MusicPlayerPlus. To download
cover art for all of the albums in your MPD music directory, run the command:

```
mpplus -D art
```

Cover art for each album is saved as the file `cover.jpg` in the album folder.
Existing cover art is preserved. If an album has incorrect album cover art and
Beets library management has been activated with `mppinit import`, update the
album cover art for that album with the command `beet fetchart -f <query>`
where `<query>` is a Beets query that identifies that album. For example,
to update the album cover art for the album "Eldorado" by Electric Light
Orchestra, issue the command `beet fetchart -f electric eldorado`.

### Custom key bindings

A few custom key bindings are configured during MusicPlayerPlus initialization
with the `mppinit` command. These are purely for convenience and can be altered
or removed if desired.

Tmux custom key bindings are defined in `$HOME/.tmux.conf`.
MusicPlayerPlus custom key bindings for tmux sessions include the following:

-   `[ Alt-PgDn ]`     - Next window
-   `[ Shift-Right ]`  - Next window
-   `[ Alt-PgUp ]`     - Previous window
-   `[ Shift-Left ]`   - Previous window
-   `[ Alt-x ]`        - Prompt to kill session
-   `[ Alt-X ]`        - Kill session
-   `[ Alt-Left ]`     - Move pane focus to left
-   `[ Alt-Right ]`    - Move pane focus to right
-   `[ Alt-Up ]`       - Move pane focus up
-   `[ Alt-Down ]`     - Move pane focus down
-   `[ Prefix q ]`     - Prompt to kill session
-   `[ Prefix Q ]`     - Kill session

The tmux prefix key is remapped from `Ctrl-b` to `Ctrl-a` and the status bar
is configured to display a `Ctrl` message when the prefix key is pressed.

The MusicPlayerPlus tmux customization enables tmux mouse mode. The mouse can
be used to select and resize tmux panes and windows.

There are hundreds of tmux key bindings. To view the currently configured
tmux key bindings, execute the command `tmux list-keys`.

Custom key bindings are also defined for the `mpcplus` music player client
command. Mpcplus custom key bindings are defined in
`$HOME/.config/mpcplus/bindings`. MusicPlayerPlus custom key bindings for
`mpcplus` include the following:

-   `[ Alt-c ]` - Display album cover art for currently playing song
-   `[ Alt-f ]` - Open the fuzzy finder to search/select media
-   `[ Alt-m ]` - Open the MPD monitor in a terminal window
-   `[ Alt-r ]` - Raise/lower the spectrum visualizer window

#### Tmux session exit issues

In addition to the `Alt-x` and `Alt-X` key bindings above to kill the current
tmux session, MusicPlayerPlus tmux key bindings include `Ctrl-a q` and
`Ctrl-a Q` which also are mapped to `kill-session` in a similar manner. This
is because some terminal emulators, in particular iTerm2, may already have key
bindings for the `Alt` key or the Meta key may be something other than `Alt`.

In a MusicPlayerPlus tmux session, if `Alt-x` and `Alt-X` do not initiate
a `kill-session` then use the configured tmux prefix key (e.g. `Ctrl-a`)
followed by `q` or `Q` to exit the current tmux session.

If a MusicPlayerPlus tmux session has been initiated over SSH using the
Terminal app on macOS then it may be necessary to configure the Terminal
profile in use to "Use Option as Meta key" in order to recognize the custom
tmux key bindings using the `Alt` key. To configure the Terminal app profile
in this manner, go to `Terminal -> Preferences -> Profiles`. Select the 
profile you are using (usually "Basic Default") and select the `Keyboard` tab.
Click the "Use Option as Meta key" checkbox and exit Terminal preferences.

## Removal

On Debian based Linux systems where the MusicPlayerPlus package was installed
using the MusicPlayerPlus Debian format package, remove the MusicPlayerPlus
package by executing the command:

```console
    sudo apt remove musicplayerplus
```
or
```console
    sudo dpkg -r musicplayerplus
```

On RPM based Linux systems where the MusicPlayerPlus package was installed
using the MusicPlayerPlus RPM format package, remove the MusicPlayerPlus
package by executing the command:

```console
    sudo yum remove MusicPlayerPlus
```
or
```console
    sudo rpm -e MusicPlayerPlus
```

On Arch based Linux systems where the MusicPlayerPlus package was installed
using the MusicPlayerPlus Pacman format package, remove the MusicPlayerPlus
package by executing the command:

```console
    sudo pacman -Rs musicplayerplus
```

The MusicPlayerPlus package can be removed by executing the "Uninstall"
script in the MusicPlayerPlus source directory:

```console
    git clone https://github.com/doctorfree/MusicPlayerPlus.git
    cd MusicPlayerPlus
    ./Uninstall
```

## Troubleshooting
Many problems encountered with MusicPlayerPlus often resolve to problems with
the underlying Linux audio configuration. As a first step in troubleshooting,
verify the audio subsystem is functioning properly. Most systems use either
ALSA or PulseAudio and there are numerous audio test guides available.

MusicPlayerPlus includes a convenience script to test the ALSA audio subsystem.
The command `alsa_audio_test` can be run to test your ALSA audio setup.
If successful you will hear the test output of the `aplay` command.
To view a `alsa_audio_test` usage message and current ALSA configuration
settings, run the command `alsa_audio_test -u`

Another source of problems to investigate is the Music Player Daemon (MPD).
This is the music streaming server that MusicPlayerPlus connects to. MPD
is run as a system service that runs automatically. You can check the status
of the MPD service by running the command `systemctl --user status mpd`.
You can restart the MPD service with `systemctl --user restart mpd.service`.
If the issue is not resolved by a restart or reboot, check the MPD log file
at `$HOME/.config/mpd/log` looking for recent failures and exceptions.

It may be the case that the root of a problem is a missing dependency.
MusicPlayerPlus should have installed any missing dependencies but one
may have been overlooked, improperly installed, or subsequently removed.
If the system logs or error output indicates something was "not found"
then check for its existence. On Debian based systems there is a nice
repository package index maintained. If a command was not found, it is
often possible to simply type that command at a shell prompt and the
Debian packaging system will be searched for any packages that contain
a command with that name. If a likely looking package is returned, the
problem may be solved by installing that package.

Finally, see the Troubleshooting section of the
[MusicPlayerPlus Wiki](https://github.com/doctorfree/MusicPlayerPlus/wiki).
for additional troubleshooting techniques and commonly resolved issues.

If an issue cannot be resolved and all troubleshooting efforts have
failed, open an issue at
[MusicPlayerPlus issues](https://github.com/doctorfree/MusicPlayerPlus/issues).
Even if you do manage to resolve an issue, it may still be helpful to
report the issue at https://github.com/doctorfree/MusicPlayerPlus/issues
so that a fix may be incorporated in the next release.

### Known issues

#### Tmux key bindings in iTerm2 terminal emulator

The `iTerm2` terminal emulator has built-in support for tmux. Several of
the iTerm2 built-in tmux key bindings conflict with and override the default
tmux key bindings and the MusicPlayerPlus custom tmux key bindings.

Unless you are quite familiar with iTerm2 and its tmux implementation, we do
not recommend using iTerm2 with MusicPlayerPlus when running tmux sessions.

MusicPlayerPlus support for iTerm2 may be forthcoming in future releases but
at this time iTerm2 is not a supported MusicPlayerPlus terminal emulator.

#### Tmux sessions over SSH to Fedora systems

A tmux session initiated over SSH to a Fedora Linux system may size the
tmux panes incorrectly. This issue is not yet understood but will hopefully
be addressed in a future release of MusicPlayerPlus. If, for example, a
`mpplus` or `mpcplus-tmux` tmux session displays the `mpcplus` pane with
a small height while the spectrum visualizer pane consumes most of the session
window, then the `mpcplus` pane will need to be resized manually.

Tmux panes can be resized either using keyboard shortcuts or with the mouse.

To resize the `mpcplus` tmux pane using the mouse, click and drag the bottom
of the upper pane in the session window. Drag the pane border down until the
`mpcplus` display of music media appears.

To resize the `mpcplus` tmux pane using keyboard shortcuts, use one of the
default tmux key bindings:

```
bind-key -r -T prefix       M-Up              resize-pane -U 5
bind-key -r -T prefix       M-Down            resize-pane -D 5
bind-key -r -T prefix       M-Left            resize-pane -L 5
bind-key -r -T prefix       M-Right           resize-pane -R 5
bind-key -r -T prefix       C-Up              resize-pane -U
bind-key -r -T prefix       C-Down            resize-pane -D
bind-key -r -T prefix       C-Left            resize-pane -L
bind-key -r -T prefix       C-Right           resize-pane -R
```

This means you can resize a pane by `<prefix>` `Alt ↓` (tmux prefix followed
by "Alt-DownArrow"). The default MusicPlayerPlus tmux prefix is `Ctrl-a` so in
order to resize the `mpcplus` pane using the keyboard, type `Ctrl-a` then type
`Alt ↓`. You can repeat `Alt ↓` several times without needing to re-type the
`Ctrl-a` prefix if you type it fast enough (about a second). If the display of 
`Ctrl` on the tmux status line disappears and you still need to resize the
`mpcplus` pane, then you will need to re-type the prefix key `Ctrl-a`.

This issue has only been detected on Fedora Linux over SSH. However, it may
occur with other systems and may not be exclusive to either SSH or Fedora.

## Infrared remote control of MPD

Advanced users may wish to add remote control capabilities to MusicPlayerPlus.
Getting IR remote control of MPD working is pretty geeky and fun. Also cool.

This can be accomplished on most Linux systems using LIRC (Linux Infrared
Remote Control). LIRC setup and usage is described at
https://wiki.archlinux.org/title/LIRC

To get started, see the
[ArchLinux Step-by-step LIRC setup guide](https://wiki.archlinux.org/title/LIRC/Quick_start_guide)
for USB IR receiver with universal remote control.

The only prerequisites are a USB IR receiver, preferably an MCE model, and
an old universal remote control you have lying around the house.

A long list of LIRC supported remotes with corresponding LIRC configurations
can be found at the
[LIRC Remotes Databass](http://lirc-remotes.sourceforge.net/remotes-table.html).


The hard part is getting the remote control device talking to the IR receiver
since there are a number of different protocols and devices supported.
The LIRC setup guide linked above has pretty good step-by-step procedures for
establishing communication between the remote and the receiver.

Once the hardware is successfully communicating, you can control MPD with `lirc`
and `mpc` by configuring lirc. For example, add the following to `~/.lircrc`:

```
## irexec
begin
     prog = irexec
     button = play_pause
     config = mpc toggle
     repeat = 0
end

begin
     prog = irexec
     button = stop
     config = mpc stop
     repeat = 0
end
begin
     prog = irexec
     button = previous
     config = mpc prev
     repeat = 0
end
begin
     prog = irexec
     button = next
     config = mpc next
     repeat = 0
end
begin
     prog = irexec
     button = volup
     config = mpc volume +2
     repeat = 1
end
begin
     prog = irexec
     button = voldown
     config = mpc volume -2
     repeat = 1
end
begin
     prog = irexec
     button = pbc
     config = mpc random
     repeat = 0
end
begin
     prog = irexec
     button = pdvd
     config = mpc update
     repeat = 0
end
begin
     prog = irexec
     button = right
     config = mpc seek +00:00:05
     repeat = 0
end
begin
     prog = irexec
     button = left
     config = mpc seek -00:00:05
     repeat = 0
end
begin
     prog = irexec
     button = up
     config = mpc seek +1%
     repeat = 0
end
begin
     prog = irexec
     button = down
     config = mpc seek -1%
     repeat = 0
end
```

A guide for configuring `lirc` to control MPD using `mpc` can be found at
https://wiki.archlinux.org/title/Music_Player_Daemon/Tips_and_tricks#Control_MPD_with_lirc

## Screenshots

<p float="left">
  <img src="https://github.com/doctorfree/MusicPlayerPlus/blob/master/screenshots/mpplus-tilix.png?raw=true"/>
  <img src="https://github.com/doctorfree/MusicPlayerPlus/blob/master/screenshots/mpplus-lyrics.png?raw=true"/>
</p>

## Videos

- [![MusicPlayerPlus Intro](https://i.imgur.com/UH2A21h.png)](https://www.youtube.com/watch?v=r7XLA9tO45Q "MusicPlayerPlus ASCIImatics Intro")
- [![MusicPlayerPlus Demo](https://i.imgur.com/ZntE1sH.jpg)](https://www.youtube.com/watch?v=y2yaHm04ELM "MusicPlayerPlus Demo")

## Building MusicPlayerPlus from source

MusicPlayerPlus can be compiled, packaged, and installed from the source code
repository. This should be done as a normal user with `sudo` privileges:

```
# Retrieve the source code from the repository
git clone https://github.com/doctorfree/MusicPlayerPlus.git
# Enter the MusicPlayerPlus source directory
cd MusicPlayerPlus
# Install the necessary build environment (not necessary on Arch Linux)
scripts/install-dev-env.sh
# Compile the MusicPlayerPlus components and create an installation package
./mkpkg
# Install MusicPlayerPlus and its dependencies
./Install
```

These steps are detailed below.

### Clone MusicPlayerPlus repository

```
git clone https://github.com/doctorfree/MusicPlayerPlus.git
cd MusicPlayerPlus
```

**[Note:]** The `mkpkg` script in the top level of the MusicPlayerPlus
repository can be used to build an installation package on all supported
platforms. After cloning, `cd MusicPlayerPlus` and `./mkpkg`. The resulting
installation package(s) will be found in `./releases/<version>/`.

### Install build dependencies

MusicPlayerPlus components have build dependencies on the following:

* libtool
* automake
* build-essentials
* [Boost library](https://www.boost.org/)
* [NCurses library](http://www.gnu.org/software/ncurses/ncurses.html)
* [Readline library](https://tiswww.case.edu/php/chet/readline/rltop.html)
* [Curl library](https://curl.haxx.se/)
* [fftw library](http://www.fftw.org/)
* [tag library](https://taglib.org/)
* [iniparser](https://github.com/ndevilla/iniparser)
* [ALSA dev files](http://alsa-project.org/)
* [Pulseaudio dev files](http://freedesktop.org/software/pulseaudio/doxygen/)
* [Eigen](http://eigen.tuxfamily.org/)
* [Gaia](https://github.com/MTG/gaia)
* [libavcodec/libavformat/libavutil/libswresample](http://ffmpeg.org/)
* [libsamplerate](http://www.mega-nerd.com/SRC/)
* [LibYAML](http://pyyaml.org/wiki/LibYAML)
* [Chromaprint](https://github.com/acoustid/chromaprint)
* [TensorFlow](https://tensorflow.org/)

Install build dependencies via:

```
scripts/install-dev-env.sh
```

or manually with:

```
sudo apt-get install \
    build-essential libeigen3-dev libfftw3-dev clang \
    libavcodec-dev libavformat-dev libavutil-dev libswresample-dev \
    libsamplerate0-dev libtag1-dev libchromaprint-dev libmpdclient-dev \
    autotools-dev autoconf libtool libboost-all-dev fftw-dev \
    libiniparser-dev libyaml-dev swig python3-dev pkg-config \
    libncurses-dev libasound2-dev libreadline-dev libpulse-dev \
    libcurl4-openssl-dev qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools \
    libavfilter-dev libavdevice-dev libsqlite3-dev
```

On RPM based systems like Fedora Linux, manually install build dependencies via:

```
sudo dnf install alsa-lib-devel ncurses-devel fftw3-devel \
     pulseaudio-libs-devel libtool automake iniparser-devel \
     SDL2-devel eigen3-devel libyaml-devel clang-devel \
     ffmpeg-devel libchromaprint-devel python-devel \
     python3-devel python3-yaml python3-six sqlite-devel
```

On Arch Linux or other PKGBUILD based Linux systems, manually install build
dependencies via:

```
sudo pacman -S --needed base-devel eigen fftw clang ffmpeg4.4 libsamplerate \
     taglib chromaprint libmpdclient boost boost-libs iniparser libyaml swig \
     alsa-lib ncurses readline libpulse libcurl-compat sqlite qt5-base \
     qt5-tools python python-numpy python-six pandoc zip
```

**[Note:]** The MusicPlayerPlus `PKGBUILD` on Arch Linux defines build
dependencies and these will be automatically installed when performing
a `makepkg` build. It is not necessary to pre-install these packages.

### Install packaging dependencies

MusicPlayerPlus components have packaging dependencies on the following:

On Debian based systems like Ubuntu Linux, install packaging dependencies via:

```
sudo apt install dpkg
```

On RPM based systems like Fedora Linux, install packaging dependencies via:

```
sudo dnf install rpm-build rpm-devel rpmlint rpmdevtools
```

### Build and package MusicPlayerPlus

To build and package MusicPlayerPlus, execute the command:

```
./mkpkg
```

On Debian based systems like Ubuntu Linux, the `mkpkg` scripts executes
`scripts/mkdeb.sh`.

On RPM based systems like Fedora Linux, the `mkpkg` scripts executes
`scripts/mkrpm.sh`.

On PKGBUILD based systems like Arch Linux, the `mkpkg` scripts executes
`scripts/mkaur.sh`.

### Install MusicPlayerPlus from source build

After successfully building and packaging MusicPlayerPlus with either
`./mkpkg`, install the MusicPlayerPlus package with the command:

```
./Install
```

## Contributing

There are a variety of ways to contribute to the MusicPlayerPlus project.
All forms of contribution are appreciated and valuable. Also, it's fun to
collaborate. Here are a few ways to contribute to the further improvement
and evolution of MusicPlayerPlus:

### Testing and Issue Reporting

MusicPlayerPlus is fairly complex with many components, features, options,
configurations, and use cases. Although currently only supported on
Linux platforms, there are a plethora of Linux platforms on which
MusicPlayerPlus can be deployed. Testing all of the above is time consuming
and tedious. If you have a Linux platform on which you can install
MusicPlayerPlus and you have the time and will to put it through its paces,
then issue reports on problems you encounter would greatly help improve the
robustness and quality of MusicPlayerPlus. Open issue reports at
[https://github.com/doctorfree/MusicPlayerPlus/issues](https://github.com/doctorfree/MusicPlayerPlus/issues)

### Sponsor MusicPlayerPlus

MusicPlayerPlus is completely free and open source software. All of the
MusicPlayerPlus components are freely licensed and may be copied, modified,
and redistributed freely. Nobody gets paid, nobody is making any money,
it's a project fully motivated by curiousity and love of music. However,
it does take some money to procure development and testing resources.
Right now MusicPlayerPlus needs a multi-boot test platform to extend support
to a wider variety of Linux platforms and potentially Mac OS X.

If you have the means and you would like to sponsor MusicPlayerPlus development,
testing, platform support, and continued improvement then your monetary
support could play a very critical role. A little bit goes a long way
in MusicPlayerPlus. For example, a bootable USB SSD device could serve as a 
means of porting and testing support for additional platforms. Or, a
decent cup of coffee could be the difference between a bug filled
release and a glorious musical adventure.

Sponsor the MusicPlayerPlus project at
[https://github.com/sponsors/doctorfree](https://github.com/sponsors/doctorfree)

### Contribute to Development

If you have programming skills and find the management and ease-of-use of
digital music libraries to be an interesting area, you can contribute to
MusicPlayerPlus development through the standard Github "fork, clone,
pull request" process. There are many guides to contributing to Github hosted
open source projects on the Internet. A good one is available at
[https://www.dataschool.io/how-to-contribute-on-github/](https://www.dataschool.io/how-to-contribute-on-github/). Another short succinct guide is at
[https://gist.github.com/MarcDiethelm/7303312](https://gist.github.com/MarcDiethelm/7303312).

Once you have forked and cloned the MusicPlayerPlus repository, it's time to
setup a development environment. Although many of the MusicPlayerPlus commands
are Bash shell scripts, there are also applicatons written in C and C++ along
with documentation in Markdown format, configuration files in a variety of
formats, examples, screenshots, video demos, build scripts, packaging, and more.

The development environment consists of several packages needed to build,
package, and test MusicPlayerPlus components. These include:

```
    build-essential libeigen3-dev libfftw3-dev clang
    libavcodec-dev libavformat-dev libavutil-dev libswresample-dev
    libsamplerate0-dev libtag1-dev libchromaprint-dev libmpdclient-dev
    autotools-dev autoconf libtool libboost-all-dev fftw-dev
    libiniparser-dev libyaml-dev swig python3-dev pkg-config
    libncurses-dev libasound2-dev libreadline-dev libpulse-dev
    libcurl4-openssl-dev qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools
    libavfilter-dev libavdevice-dev libsqlite3-dev
```

Utilities and applications built from source in MusicPlayerPlus include:

- mppcava character based spectrum visualizer

The build scripts in the `scripts/` directory of the MusicPlayerPlus
repository can be used to compile bliss-analyze, blissify, and mppcava.
These are:

- scripts/build-bliss-analyze.sh
- scripts/build-blissify.sh
- scripts/build-mppcava.sh

Invoke the appropriate build script for the utility you wish to compile.
For example, to compile the `mppcava` spectrum visualizer from source, run the command:

```
./scripts/build-mppcava.sh
```

On Debian (e.g. Ubuntu), PKGBUILD (e.g. Arch) and RPM (e.g. Fedora) based
systems the MusicPlayerPlus installation package can be created with the
`mkpkg` scripts. The `mkpkg` script determines which platform it is on
and executes the appropriate build and packaging script in the `scripts/`
directory. These scripts invoke the build scripts for each of the projects
included with MusicPlayerPlus, populate a distribution tree, and call the
respective packaging utilities. Packages are saved in the
`./releases/<version>/` folder. Once a package has been created
it can be installed with the `Install` script.

It's not necessary to have C/C++ expertise to contribute to MusicPlayerPlus
development. Many of the MusicPlayerPlus commands are Bash scripts and require
no compilaton. Script commands reside in the `bin` and `share/scripts`
directories. To modify a shell script, install MusicPlayerPlus and edit the
`bin/<script>` or `share/scripts/<script.sh>` you wish to improve. After making
your changes simply copy the revised script to `/usr/bin` and test your changes.

Modifying the configuration files is a little more tricky. Configuration
files generally live in the `config` directory but each has its own installation
location and some are modified by the `mppinit` command during installation.
If you are just modifying the shell scripts or configuration files then
you don't need to worry about the extensive list of dependencies listed above.

Feel free to email me at github@ronrecord.com with questions or comments.

## See also

- [Asciiville](Asciiville.md)
- [DriveCommandLine](DriveCommandLine.md)
- [MagicMirror](MagicMirror.md)
- [MirrorCommand](MirrorCommand.md)
- [RoonCommandLine](RoonCommandLine.md)
