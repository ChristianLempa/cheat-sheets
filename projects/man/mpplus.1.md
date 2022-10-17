---
title: MPPLUS
section: 1
header: User Manual
footer: mpplus 2.0.1
date: December 05, 2021
---
## NAME
mpplus - Launch an MPD music player client and spectrum visualizer

## SYNOPSIS
**mpplus** [-A on|off] [-a] [-b] [-B] [-c] [-C client] [-D art|bandcamp|soundcloud] [-d music_directory] [-E] [-e] [-F] [-f] [-G] [-g] [-h] [-I] [-i] [-jJ] [-k] [-K] [-L] [-m] [-n num] [-M alsaconf|enable|disable|restart|start|stop|status] [-N] [-p] [-P script] [-q] [-r] [-R] [-s song] [-S] [-t] [-T on|off] [-u] [-U] [-v viz_comm] [-w|W] [-x query] [-X query] [-y] [-Y] [-z fzmpopt]

## DESCRIPTION
The *mpplus* command acts as a front-end for launching the mpcplus music player client and a spectrum visualizer in various terminal emulators and window placements. It can be used to display these utilities juxtaposed in separate windows or fullscreen overlayed with transparency. Alternately, mpplus can launch any specified MPD client along with a specified spectrum visualizer (`mppcava` spectrum visualizer is used by default). Command line options also support running the *mpplus* windows in a tmux session and recording that session using *asciinema*.

The *mpplus* command can be used to control the *mpd* and *mpd.socket* system services when invoked with the `-M action` command line option. The Music Player Daemon (MPD) can be started, stopped, enabled, disabled, restarted, and status queried.

The *mpplus* command can also act as a front-end to the *mppsplash* and *mppsplash-tmux* commands when invoked with the `-S` and `-T on` command line options.

The *mpplus* command can be used in conjunction with the Beets music library management system:

- When invoked as `mpplus -D art` it will downlad album cover art for all albums in the music library
- When invoked as `mpplus -D bandcamp` it will downlad songs from Bandcamp
- When invoked as `mpplus -D soundcloud` it will downlad songs from Soundcloud
- When invoked as `mpplus -F` it will convert WAV format files in the music library to MP3 format files
- When invoked as `mpplus -G` it will convert M4A format files in the music library to MP3 format files
- When invoked as `mpplus -I` it will perform a Beets library import of all songs and albums in the music library. If a previous import has been performed it will import any new songs or albums it finds in the music library.
- When invoked as `mpplus -L` it will downlad lyrics for all songs in the music library that do not already have lyrics

When invoked with the `-i` option, `mpplus` presents a selection menu and operates in interactive mode.

Occasionally a tmux session or asciimatics script will hang. Previously started tmux sessions and asciimatics scripts can be quickly and easily killed by executing the `mpplus -K` command.

## COMMAND LINE OPTIONS

*MPCplus/Visualizer options:*

**-A 'on|off'**
: Specifies whether to display album cover art

**-c**
: Indicates use current terminal emulator / console mode

**-C 'client'**
: Indicates use 'client' MPD client rather than mpcplus

**-e**
: indicates use simple terminal emulator

**-E**
: Indicates do not use gradient colors for spectrum visualizer

**-f**
: Indicates fullscreen display

**-g**
: Indicates use gnome terminal emulator

**-h**
: Indicates half-height for mppcava window (with -f only)

**-k**
: Indicates use kitty terminal emulator

**-P script**
: Specifies the ASCIImatics script to run in visualizer pane

**-q**
: Indicates quarter-height for mppcava window (with -f only)

**-r**
: Indicates use retro terminal emulator

**-t**
: Indicates use tilix terminal emulator

**-v 'viz_comm'**
: Indicates use visualizer 'viz_comm' rather than mppcava

*ASCIImatics animation options:*

**-a**
: Indicates play audio during ASCIImatics display

**-b**
: Indicates use backup audio during ASCIImatics display

**-j**
: Indicates use Julia Set scenes in ASCIImatics display

**-J**
: Indicates Julia Set with several runs using different parameters

**-m**
: Indicates use MusicPlayerPlus scenes in ASCIImatics display

**-n num**
: Specifies the number of times to cycle ASCIImatics scenes

**-N**
: Indicates use alternate comments in Plasma ASCIImatics scenes

**-p**
: Indicates use Plasma scenes in ASCIImatics display

**-s song**
: Specifies a song to accompany an ASCIImatics animation

**-S**
: Indicates display ASCIImatics splash animation

*General options:*

**-B**
: Uses Blissify to create audio-based information in a song similarity database for all music library media.

**-D art**
: Indicates download album cover art and exit

**-D bandcamp**
: Indicates download songs from Bandcamp and exit

**-D soundcloud**
: Indicates download songs from Soundcloud and exit

**-d 'music_directory'**
: Specifies the music directory to use for downloaded album cover art (without this option -D will use the `MUSIC_DIR` setting in `~/.config/mpprc`

**-F**
: Indicates convert all WAV format files in the music library to MP3 format files and exit. A subsequent 'mpplus -I' import will be necessary to import these newly converted music files.

**-G**
: Indicates convert all M4A format files in the music library to MP3 format files and exit. A subsequent 'mpplus -I' import will be necessary to import these newly converted music files.

**-I**
: Indicates import albums and songs from 'music_directory' to Beets and exit

**-i**
: Indicates interactive mode with selection menus

**-K**
: Indicates kill MusicPlayerPlus tmux sessions and ASCIImatics scripts

**-L**
: Indicates download lyrics to the Beets library and exit

**-M 'enable|disable|start|stop|restart|status'**
: Enable, disable, start, stop, restart, or get the status of the MPD and MPD socket system services 

**-R**
: Indicates record tmux session with asciinema. Asciinema is not installed by MusicPlayerPlus. To record tmux sessions with asciinema, use your system's package manager to install it (e.g. apt install asciinema)

**-T 'on|off'**
: Specifies whether to use a tmux session

**-U**
: Use `tmuxp` to manage `tmux` sessions

**-w**
: Indicates write metadata during Beets import

**-W**
: Indicates do not write metadata during Beets import

**-x 'query'**
: Uses AcousticBrainz to retrieve audio-based information for all music library media matching 'query'. A query of 'all' performs the retrieval on the entire music library.

**-X 'query'**
: Performs an analysis and retrieval, using Essentia, of audio-based information for all music library media matching 'query'. A query of 'all' performs the analysis and retrieval on the entire music library.

**-Y**
: Initializes the YAMS last.fm scrobbler service

**-y**
: Disables the YAMS last.fm scrobbler service

**-z opt**
: Specifies an `fzmp` option and invokes `fzmp` to list/search/select MPD media. Valid values for `opt` are 'a', 'A', 'g', 'p', or 'P'

**-u**
: Displays this usage message and exits

## EXAMPLES
**mpplus**
: Launches `mpcplus` music player client running in the kitty terminal emulator with mppcava spectrum visualizer running in another kitty window. 

**mpplus -i**
: Launches `mpplus` in interactive mode with menu selections controlling actions rather than command line arguments

**mpplus -r**
: Launches `mpcplus` music player client running in cool-retro-term terminal emulator with mppcava spectrum visualizer running in a kitty terminal emulator window. 

**mpplus -C cantata**
: Launches `cantata` music player client running in a separate window with mppcava spectrum visualizer running in a kitty terminal emulator window. 

**mpplus -C cmus**
: Launches the `cmus` music player client with mppcava spectrum visualizer running in a kitty terminal emulator window. 

**mpplus -C mcg**
: Launches the CoverGrid music player client (`mcg`) running in a separate window with mppcava spectrum visualizer running in a kitty terminal emulator window. 

**mpplus -f -q -t**
: Launches `mpcplus` music player client in fullscreen mode with mppcava spectrum visualizer in quarter-screen mode, both running in a tilix terminal emulator window. 

**mpplus -a -T on**
: Launches `mpcplus` music player client and visualizer running in a tmux session displaying album cover art. 

**mpplus -M stop**
: Stops the Music Player Daemon service and the associated MPD socket service

**mpplus -R -T on**
: Creates an asciinema recording of `mpcplus` music player client and visualizer running in a tmux session

**mpplus -S -j -a**
: Launch `mppsplash` displaying the Julia Set asciimatics animation with audio

**mpplus -D art**
: Download album cover art for any albums in the music library that do not already have cover art 

**mpplus -D soundcloud**
: Download favorited songs from Soundcloud

**mpplus -I**
: Import the music library into the Beets library management system

**mpplus -I -W**
: Import the music library into the Beets library management system, do not write metadata

**mpplus -L**
: Download lyrics for any songs in the music library that do not already have lyrics

**mpplus -X all**
: Analyze audio using Essentia and retrieve information for the entire music library

**mpplus -x all**
: Retrieve audio information for the entire music library using AcousticBrainz

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPPLUS is distributed under an Open Source license.
See the file LICENSE in the MPPLUS source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPLUS and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mppcava**(1), **mppsplash**(1), **mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

