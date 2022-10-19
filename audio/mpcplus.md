# Mpcplus – featureful NCurses based MPD client

[![License: GPL v2](https://img.shields.io/badge/License-GPL_v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

The `mpcplus` NCurses MPD client is derived from `ncmpcpp` and customized
for integration with [MusicPlayerPlus](../projects/MusicPlayerPlus.md).

Many enhancements to `mpcplus` are included in the `MusicPlayerPlus` project.
These include the display of album cover art in a `tmux` session along side
`mpcplus`, the frequency spectrum visualizer `mppcava`, and many more.

Repository: https://github.com/doctorfree/mpcplus

## Table of Contents

1. [Main features](#main-features)
1. [Requirements](#requirements)
1. [Required setup](#required-setup)
1. [Installation](#installation)
1. [Post Installation Configuration](#post-installation-configuration)
1. [Removal](#removal)
1. [Screenshots](#screenshots)
1. [Videos](#videos)
1. [Cheat sheet](#cheat-sheet)

## Main features

* tag editor
* playlist editor
* easy to use search engine
* media library
* integration with external spectrum visualizer
* ability to fetch song lyrics from a variety of sources
* ability to fetch artist info from last.fm
* new display mode
* alternative user interface
* ability to browse and add files from outside of MPD music directory

…and a lot more minor functions.

## Requirements

MusicPlayerPlus is compiled and packaged for installation on:

- Arch Linux (x86_64)
- CentOS Linux (x86_64)
- Fedora Linux (x86_64)
- Raspberry Pi OS (armhf)
- Ubuntu Linux (amd64)

## Required setup

* Install, configure, and activate the Music Player Daemon (MPD)
    * The [MusicPlayerPlus](https://github.com/doctorfree/MusicPlayerPlus) package installs and automatically configures MPD
* Create a music library if you do not already have one
    * Default `mpcplus` location for the music library is `$HOME/Music`
    * Recommended structure of the music library is `artist/album/songs`
* Install the latest Arch, Debian, or RPM format installation package from the [Mpcplus Releases](https://github.com/doctorfree/mpcplus/releases) page
* Run the `mpcinit` command as your normal user

## Installation

Mpcplus v1.0.0 and later can be installed on Linux systems using
the Arch packaging format, the Debian packaging format, or the Red Hat
Package Manager (RPM).

### Supported platforms

Mpcplus has been tested successfully on the following platforms:

- **Arch Linux 2022.07.01**
    - `mpcplus_<version>-<release>-x86_64.pkg.tar.zst`
- **Ubuntu Linux 20.04**
    - `mpcplus_<version>-<release>.amd64.deb`
- **Fedora Linux 36**
    - `mpcplus_<version>-<release>.x86_64.rpm`
- **CentOS Linux 8**
    - `mpcplus_<version>-<release>.x86_64.rpm`
- **Raspbian Linux 11**
    - `mpcplus_<version>-<release>.armhf.deb`

### Debian package installation

Many Linux distributions, most notably Ubuntu and its derivatives, use the
Debian packaging system.

To tell if a Linux system is Debian based it is usually sufficient to
check for the existence of the file `/etc/debian_version` and/or examine the
contents of the file `/etc/os-release`.

To install on a Debian based Linux system, download the latest Debian format
package from the
[mpcplus Releases](https://github.com/doctorfree/mpcplus/releases).

Install the mpcplus package by executing the command

```console
sudo apt install ./mpcplus_<version>-<release>.amd64.deb
```
or
```console
sudo dpkg -i ./mpcplus_<version>-<release>.amd64.deb
```

or, on a Raspberry Pi:

```console
sudo apt install ./mpcplus_<version>-<release>.armhf.deb
```
or
```console
sudo dpkg -i ./mpcplus_<version>-<release>.armhf.deb
```

**NOTE:** In some cases you may see a warning message when installing the
Debian package. The message:

Repository is broken: mpcplus:amd64 (= <version-<release>) has no Size information

can safely be ignored. This is an issue with the Debian packaging system
and has no effect on the installation.

### RPM Package installation

Red Hat Linux, SUSE Linux, and their derivatives use the RPM packaging
format. RPM based Linux distributions include Fedora, AlmaLinux, CentOS,
openSUSE, OpenMandriva, Mandrake Linux, Red Hat Linux, and Oracle Linux.

To install on an RPM based Linux system, download the latest RPM format
package from the
[mpcplus Releases](https://github.com/doctorfree/mpcplus/releases).

Install the mpcplus package by executing the command

```console
sudo yum localinstall ./mpcplus_<version>-<release>.x86_64.rpm
```
or
```console
sudo rpm -i ./mpcplus_<version>-<release>.x86_64.rpm
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
[mpcplus Releases](https://github.com/doctorfree/mpcplus/releases).

Install the mpcplus package by executing the command

```console
sudo pacman -U ./mpcplus_<version>-<release>-x86_64.pkg.tar.zst
```

## Post Installation Configuration

If not already configured, the MPD server will need to know where to
locate your music library. This can be configured by editing the MPD
configuration file `/etc/mpd.conf` or `~/.config/mpd/mpd.conf` and
running the command `mpcinit sync`.

### Client Configuration (required)

Initialize the `mpcplus` client configuration by executing the command:

```
mpcinit
```

Examine the generated `mpcplus` configuration in `~/.config/mpcplus/config`
and `~/.config/mpcplus/bindings` and make any desired changes.

### Usage

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

The usage messages for `mpcinit` and `mpcplus`
provide a brief summary of the command line options.

The `mpcinit` performs one-time initializations:

```
Usage: mpcinit [-o] [-q] [-r] [-U] [-y] [-u] [mpd|sync]
Where:
	'-o' indicates overwrite any pre-existing configuration
	'-q' indicates quiet execution, no status messages
	'-y' indicates answer 'yes' to all and proceed
	'-u' displays this usage message and exits

	'mpd' activates the MPD music server
	'sync' synchronizes mpcplus configuration across configs

'mpcinit' must be run as the mpcplus user, not root.
```

The `mpcplus` command is an MPD client and acts as the primary
mpcplus music player:

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
**[mpcpluskeys man page](mpcpluskeys.1.md)**
with the command `man mpcpluskeys`.

## Removal

On Debian based Linux systems where the mpcplus package was installed
using the mpcplus Debian format package, remove the mpcplus
package by executing the command:

```console
    sudo apt remove mpcplus
```
or
```console
    sudo dpkg -r mpcplus
```

On RPM based Linux systems where the mpcplus package was installed
using the mpcplus RPM format package, remove the mpcplus
package by executing the command:

```console
    sudo yum remove mpcplus
```
or
```console
    sudo rpm -e mpcplus
```

On Arch based Linux systems where the mpcplus package was installed
using the mpcplus Pacman format package, remove the mpcplus
package by executing the command:

```console
    sudo pacman -Rs mpcplus
```

The mpcplus package can be removed by executing the "Uninstall"
script in the mpcplus source directory:

```console
    git clone https://github.com/doctorfree/mpcplus.git
    cd mpcplus
    ./Uninstall
```

## Screenshots

<img src="https://github.com/doctorfree/mpcplus/blob/master/screenshots/mpplus-tilix.png?raw=true"/>
<img src="https://github.com/doctorfree/mpcplus/blob/master/screenshots/mpplus-lyrics.png?raw=true"/>

## Videos

- [![Mpcplus Demo](https://i.imgur.com/ZntE1sH.jpg)](https://www.youtube.com/watch?v=y2yaHm04ELM "Mpcplus Demo")

## Cheat sheet

```
## Keys - Movement

-   <span class="kbd">Up k</span> - Move cursor up
-   <span class="kbd">Down j</span> - Move cursor down
-   <span class="kbd">\[</span> - Move cursor up one album
-   <span class="kbd">\]</span> - Move cursor down one album
-   <span class="kbd">{</span> - Move cursor up one artist
-   <span class="kbd">}</span> - Move cursor down one artist
-   <span class="kbd">Page Up</span> - Page up
-   <span class="kbd">Page Down</span> - Page down
-   <span class="kbd">Home</span> - Home
-   <span class="kbd">End</span> - End
-   <span class="kbd">Tab</span> - Switch to next screen in sequence
-   <span class="kbd">Shift-Tab</span> - Switch to previous screen in
    sequence
-   <span class="kbd">F1</span> - Show help
-   <span class="kbd">1</span> - Show playlist
-   <span class="kbd">2</span> - Show browser
-   <span class="kbd">3</span> - Show search engine
-   <span class="kbd">4</span> - Show media library
-   <span class="kbd">5</span> - Show playlist editor
-   <span class="kbd">6</span> - Show tag editor
-   <span class="kbd">7</span> - Show outputs
-   <span class="kbd">8</span> - Show music visualizer
-   <span class="kbd">=</span> - Show clock
-   <span class="kbd">@</span> - Show server info

## Keys - Global

-   <span class="kbd">s</span> - Stop
-   <span class="kbd">p</span> - Pause
-   <span class="kbd">&gt;</span> - Next track
-   <span class="kbd">&lt;</span> - Previous track
-   <span class="kbd">Ctrl-H Backspace</span> - Replay playing song
-   <span class="kbd">f</span> - Seek forward in playing song
-   <span class="kbd">b</span> - Seek backward in playing song
-   <span class="kbd">- Left</span> - Decrease volume by 2%
-   <span class="kbd">Right +</span> - Increase volume by 2%
-   <span class="kbd">t</span> - Toggle space mode (select/add)
-   <span class="kbd">T</span> - Toggle add mode (add or remove/always
    add)
-   <span class="kbd">|</span> - Toggle mouse support
-   <span class="kbd">v</span> - Reverse selection
-   <span class="kbd">V</span> - Remove selection
-   <span class="kbd">B</span> - Select songs of album around the cursor
-   <span class="kbd">a</span> - Add selected items to playlist
-   <span class="kbd">\`</span> - Add random items to playlist
-   <span class="kbd">r</span> - Toggle repeat mode
-   <span class="kbd">z</span> - Toggle random mode
-   <span class="kbd">y</span> - Toggle single mode
-   <span class="kbd">R</span> - Toggle consume mode
-   <span class="kbd">Y</span> - Toggle replay gain mode
-   <span class="kbd">\#</span> - Toggle bitrate visibility
-   <span class="kbd">Z</span> - Shuffle playlist
-   <span class="kbd">x</span> - Toggle crossfade mode
-   <span class="kbd">X</span> - Set crossfade
-   <span class="kbd">u</span> - Start music database update
-   <span class="kbd">:</span> - Execute command
-   <span class="kbd">Ctrl-F</span> - Apply filter
-   <span class="kbd">/</span> - Find item forward
-   <span class="kbd">?</span> - Find item backward
-   <span class="kbd">,</span> - Jump to previous found item
-   <span class="kbd">.</span> - Jump to next found item
-   <span class="kbd">w</span> - Toggle find mode (normal/wrapped)
-   <span class="kbd">G</span> - Locate song in browser
-   <span class="kbd">~</span> - Locate song in media library
-   <span class="kbd">Ctrl-L</span> - Lock/unlock current screen
-   <span class="kbd">Left h</span> - Switch to master screen (left one)
-   <span class="kbd">Right l</span> - Switch to slave screen (right
    one)
-   <span class="kbd">E</span> - Locate song in tag editor
-   <span class="kbd">P</span> - Toggle display mode
-   <span class="kbd">\\</span> - Toggle user interface
-   <span class="kbd">!</span> - Toggle displaying separators between
    albums
-   <span class="kbd">g</span> - Jump to given position in playing song
    (formats: mm:ss, x%)
-   <span class="kbd">i</span> - Show song info
-   <span class="kbd">I</span> - Show artist info
-   <span class="kbd">L</span> - Toggle lyrics fetcher
-   <span class="kbd">F</span> - Toggle fetching lyrics for playing
    songs in background
-   <span class="kbd">q</span> - Quit

## Keys - Playlist

-   <span class="kbd">Enter</span> - Play selected item
-   <span class="kbd">Delete</span> - Delete selected item(s) from
    playlist
-   <span class="kbd">c</span> - Clear playlist
-   <span class="kbd">C</span> - Clear playlist except selected item(s)
-   <span class="kbd">Ctrl-P</span> - Set priority of selected items
-   <span class="kbd">Ctrl-K m</span> - Move selected item(s) up
-   <span class="kbd">n Ctrl-J</span> - Move selected item(s) down
-   <span class="kbd">M</span> - Move selected item(s) to cursor
    position
-   <span class="kbd">A</span> - Add item to playlist
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">S</span> - Save playlist
-   <span class="kbd">Ctrl-V</span> - Sort playlist
-   <span class="kbd">Ctrl-R</span> - Reverse playlist
-   <span class="kbd">o</span> - Jump to current song
-   <span class="kbd">U</span> - Toggle playing song centering

## Keys - Browser

-   <span class="kbd">Enter</span> - Enter directory/Add item to
    playlist and play it
-   <span class="kbd">Space</span> - Add item to playlist/select it
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">e</span> - Edit directory name
-   <span class="kbd">e</span> - Edit playlist name
-   <span class="kbd">2</span> - Browse MPD database/local filesystem
-   <span class="kbd">\`</span> - Toggle sort mode
-   <span class="kbd">o</span> - Locate playing song
-   <span class="kbd">Ctrl-H Backspace</span> - Jump to parent directory
-   <span class="kbd">Delete</span> - Delete selected items from disk
-   <span class="kbd">G</span> - Jump to playlist editor (playlists
    only)

## Keys - Search engine

-   <span class="kbd">Enter</span> - Add item to playlist and play
    it/change option
-   <span class="kbd">Space</span> - Add item to playlist
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">y</span> - Start searching
-   <span class="kbd">3</span> - Reset search constraints and clear
    results

## Keys - Media library

-   <span class="kbd">4</span> - Switch between two/three columns mode
-   <span class="kbd">Left h</span> - Previous column
-   <span class="kbd">Right l</span> - Next column
-   <span class="kbd">Enter</span> - Add item to playlist and play it
-   <span class="kbd">Space</span> - Add item to playlist
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">e</span> - Edit tag (left column)/album
    (middle/right column)
-   <span class="kbd">\`</span> - Toggle type of tag used in left column
-   <span class="kbd">m</span> - Toggle sort mode

## Keys - Playlist editor

-   <span class="kbd">Left h</span> - Previous column
-   <span class="kbd">Right l</span> - Next column
-   <span class="kbd">Enter</span> - Add item to playlist and play it
-   <span class="kbd">Space</span> - Add item to playlist/select it
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">e</span> - Edit playlist name
-   <span class="kbd">Ctrl-K m</span> - Move selected item(s) up
-   <span class="kbd">n Ctrl-J</span> - Move selected item(s) down
-   <span class="kbd">Delete</span> - Delete selected playlists (left
    column)
-   <span class="kbd">C</span> - Clear playlist except selected item(s)
-   <span class="kbd">Ctrl-P</span> - Set priority of selected items
-   <span class="kbd">Ctrl-K m</span> - Move selected item(s) up
-   <span class="kbd">n Ctrl-J</span> - Move selected item(s) down
-   <span class="kbd">M</span> - Move selected item(s) to cursor
    position
-   <span class="kbd">A</span> - Add item to playlist
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">S</span> - Save playlist
-   <span class="kbd">Ctrl-V</span> - Sort playlist
-   <span class="kbd">Ctrl-R</span> - Reverse playlist
-   <span class="kbd">o</span> - Jump to current song
-   <span class="kbd">U</span> - Toggle playing song centering

## Keys - Browser

-   <span class="kbd">Enter</span> - Enter directory/Add item to
    playlist and play it
-   <span class="kbd">Space</span> - Add item to playlist/select it
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">e</span> - Edit directory name
-   <span class="kbd">e</span> - Edit playlist name
-   <span class="kbd">2</span> - Browse MPD database/local filesystem
-   <span class="kbd">\`</span> - Toggle sort mode
-   <span class="kbd">o</span> - Locate playing song
-   <span class="kbd">Ctrl-H Backspace</span> - Jump to parent directory
-   <span class="kbd">Delete</span> - Delete selected items from disk
-   <span class="kbd">G</span> - Jump to playlist editor (playlists
    only)

## Keys - Search engine

-   <span class="kbd">Enter</span> - Add item to playlist and play
    it/change option
-   <span class="kbd">Space</span> - Add item to playlist
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">y</span> - Start searching
-   <span class="kbd">3</span> - Reset search constraints and clear
    results

## Keys - Media library

-   <span class="kbd">4</span> - Switch between two/three columns mode
-   <span class="kbd">Left h</span> - Previous column
-   <span class="kbd">Right l</span> - Next column
-   <span class="kbd">Enter</span> - Add item to playlist and play it
-   <span class="kbd">Space</span> - Add item to playlist
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">e</span> - Edit tag (left column)/album
    (middle/right column)
-   <span class="kbd">\`</span> - Toggle type of tag used in left column
-   <span class="kbd">m</span> - Toggle sort mode

## Keys - Playlist editor

-   <span class="kbd">Left h</span> - Previous column
-   <span class="kbd">Right l</span> - Next column
-   <span class="kbd">Enter</span> - Add item to playlist and play it
-   <span class="kbd">Space</span> - Add item to playlist/select it
-   <span class="kbd">e</span> - Edit song
-   <span class="kbd">e</span> - Edit playlist name
-   <span class="kbd">Ctrl-K m</span> - Move selected item(s) up
-   <span class="kbd">n Ctrl-J</span> - Move selected item(s) down
-   <span class="kbd">Delete</span> - Delete selected playlists (left
    column)
-   <span class="kbd">Delete</span> - Delete selected item(s) from
    playlist (right column)
-   <span class="kbd">c</span> - Clear playlist
-   <span class="kbd">C</span> - Clear playlist except selected items

## Keys - Lyrics

-   <span class="kbd">Space</span> - Toggle reloading lyrics upon song
    change
-   <span class="kbd">e</span> - Open lyrics in external editor
-   <span class="kbd">\`</span> - Refetch lyrics

## Keys - Tiny tag editor

-   <span class="kbd">Enter</span> - Edit tag
-   <span class="kbd">y</span> - Save

## Keys - Tag editor

-   <span class="kbd">Enter</span> - Edit tag/filename of selected item
    (left column)
-   <span class="kbd">Enter</span> - Perform operation on all/selected
    items (middle column)
-   <span class="kbd">Space</span> - Switch to albums/directories view
    (left column)
-   <span class="kbd">Space</span> - Select item (right column)
-   <span class="kbd">Left h</span> - Previous column
-   <span class="kbd">Right l</span> - Next column
-   <span class="kbd">Ctrl-H Backspace</span> - Jump to parent directory
    (left column, directories view)
```

## See also

- [mpcinit.1](mpcinit.1.md)
- [mpcplus.1](mpcplus.1.md)
- [mpcpluskeys.1](mpcpluskeys.1.md)
- [MusicPlayerPlus](../projects/MusicPlayerPlus.md)
