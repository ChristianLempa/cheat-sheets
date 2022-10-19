# Beets media library management

## Table of contents

1. [Overview](#overview)
1. [Getting started with Beets](#getting-started-with-beets)
    1. [Quickstart with Beets](#quickstart-with-beets)
    1. [Create a music library](#create-a-music-library)
    1. [Configure the music library location](#configure-the-music-library-location)
    1. [Initializing the Beets media library management system](#initializing-the-beets-media-library-management-system)
    1. [Additional Beets metadata analysis and retrieval](#additional-beets-metadata-analysis-and-retrieval)
        1. [Remove duplicate tracks](#remove-duplicate-tracks)
        1. [Rename tracks that were duplicates](#rename-tracks-that-were-duplicates)
        1. [Retrieve genres from Last.fm](#retrieve-genres-from-lastfm)
        1. [Analyze and extract additional metadata with Essentia](#analyze-and-extract-additional-metadata-with-essentia)
    1. [Convert WAV format media files](#convert-wav-format-media-files)
    1. [Import the music library into Beets](#import-the-music-library-into-beets)
    1. [Beets import followup steps](#beets-import-followup-steps)
        1. [Performing an interactive Beets import](#performing-an-interactive-beets-import)
        1. [Performing a Beets import with a MusicBrainz ID](#performing-a-beets-import-with-a-musicbrainz-id)
    1. [Downloading album cover art with the mpplus command](#downloading-album-cover-art-with-the-mpplus-command)
    1. [Downloading album cover art with the fetchart Beets plugin](#downloading-album-cover-art-with-the-fetchart-beets-plugin)
1. [Playlist creation](#playlist-creation)
1. [Fetching lyrics](#fetching-lyrics)
1. [Finding duplicate tracks](#finding-duplicate-tracks)
1. [Automated audio analysis and audio-based information retrieval](#automated-audio-analysis-and-audio-based-information-retrieval)
    1. [MusicPlayerPlus custom xtractor metadata configuration](#musicplayerplus-custom-xtractor-metadata-configuration)
    1. [MusicPlayerPlus acousticbrainz metadata configuration](#musicplayerplus-acousticbrainz-metadata-configuration)
1. [Configuring the Discogs metadata source](#configuring-the-discogs-metadata-source)
1. [MusicPlayerPlus Beets plugins](#musicplayerplus-beets-plugins)
1. [See also](#see-also)

## Overview

MusicPlayerPlus includes integrated installation and extensive configuration
for the Beets media library management system. Beets is an open source,
extensible, highly configurable suite of tools and plugins that organizes
and improves the structure, cataloging, and metadata of a music library.

Management of your music library with Beets is an optional feature provided
by MusicPlayerPlus. Although optional, use of Beets can enhance your
music library in ways that make it more useful and easier to access with
the `mpcplus` MusicPlayerPlus MPD client. For example, one of the automated
tasks that Beets performs is updating the tags in your music library. Beets
queries online sources like MusicBrainz, Bandcamp, and Last.fm to update the
music library with widely used metadata for songs and albums it can identify.
Subsequent invocations of `mpcplus` will be able to use this rich set of tags
to filter, search, and find items in your music library.

The primary source of online data for Beets is
[MusicBrainz](https://musicbrainz.org), a collaborative music database.
As of March 2022, MusicBrainz contained information on roughly 1.9 million
artists, 3 million releases, and 26.5 million recordings. This extensive set
of data, along with additional data from other online sources like
[Bandcamp](https://bandcamp.com) and [Last.fm](https://www.last.fm)
can be used to significantly improve the metadata content and organization
of your music library.

**[NOTE:]** Beets is NOT the now defunct music service purchased by Apple.
It is an open source media library management system.

## Getting started with Beets

MusicPlayerPlus has integrated Beets initialization and use into the `mppinit`
initialization command and the `mpplus` primary user interface. Due to its
complexity, flexibility, and power, Beets can be fairly difficult to manage.
MusicPlayerPlus attempts to ease the task of managing your music library
with Beets. The following few steps are all that is necessary to get started
with Beets after installing MusicPlayerPlus and initializing with `mppinit`.

### Quickstart with Beets

After installing MusicPlayerPlus and running `mppinit` some common additional
setup steps that can be performed include:

- Configuring the music library location
- Converting WAV format media files to MP3 format
- Importing a music library into the Beets library management system
- Downloading album cover art
- Downloading additional lyrics
- Activation of YAMS scrobbler for Last.fm
- Analysis and retrieval of audio-based information for media matching a query

Configure the music library location by editing `~/.config/mpd/mpd.conf` and
setting the `music_directory` to your music library location (default setting
is `~/Music`). If you change the `music_directory` setting in mpd.conf then
run the command `mppinit sync`.

The following optional post-initialization steps can be performed individually
as described below or they can be performed in two steps using `mppinit`:

```
mppinit import
```

When the import is complete

```
mppinit metadata
```

The `mppinit import` command downloads album cover art, converts any
WAV format media to MP3 format, and imports the music library into Beets.
The `mppinit metadata` command identifies and deletes duplicate tracks,
retrieves album genres from Last.fm, and optionally analyzes and
retrieves metadata for all songs in the music library.

Album cover art can be downloaded with the command `mpplus -D`.

Convert WAV format media files in your library to MP3 format files with
the command `mpplus -F`. Conversion from WAV to MP3 allows these files to
be imported into the Beets media library management system.

If you wish to manage your music library with Beets, import the music library
with the command `mpplus -I`.

Download additional lyrics with the command `mpplus -L`.

Activate the YAMS scrobbler for Last.fm with the command `mpplus -Y`.

Analysis and retrieval of audio-based information can be performed with
the command `mpplus -X 'query'` where 'query' is a Beets library query.
The special query term 'all' indicates the entire music library, i.e.
`mpplus -X all`.

#### Quickstart summary

To summarize, a MusicPlayer quickstart can be accomplished by:

* Install the latest Debian or RPM format installation package
* Run the `mppinit` command as your normal user
* If the music library is not located at `$HOME/Music`:
    * Configure the `music_directory` setting by editing `~/.config/mpd/mpd.conf`
    * Run the command `mppinit sync`
* Optionally:
    * Perform these three steps with the command `mppinit import`
        * Download album cover art with the command `mpplus -D`
        * Convert WAV format files to MP3 format with the command `mpplus -F`
        * Import your music library into Beets with the command `mpplus -I`
    * Perform these steps with the command `mppinit metadata`
        * Remove duplicate tracks with the command `beet duplicates -d`
        * Rename tracks left after duplicate removal with `beet move`
        * Analyze and retrieve audio-based information with a command like:
            * `mpplus -X 'query'` where 'query' is a Beets library query
            * `mpplus -X all` indicating analyze the entire Beets library
    * Activate the YAMS scrobbler for Last.fm with the command `mpplus -Y`
    * Download additional lyrics with the command `mpplus -L`

After initializing the Beets media library management system try playing
something with a command like:

```
beet play QUERY
```

Where 'QUERY' is a valid Beets query. This can be a simple string like
"blue" or "love" or a more complicated expression as described in the
Beets query documentation. The Beets `play` plugin should match the
query string to songs in your music library, add those songs to the
MPD queue, and play them. Use `beet ls QUERY` to see what would be played.

### Create a music library

If you do not already have one, create a music library on the system where
MusicPlayerPlus is installed. This is the music library that MPD will be
accessing and its location is defined in `$HOME/.config/mpd/mpd.conf`.
The default location for the music library is `$HOME/Music/`. If you wish
to store your music library in another location, e.g. on an external drive,
then there will be a couple of extra steps to perform, outlined below.

It is recommended to organize the music library with a structure like
`Artist/Album/songs` but this is not necessary. One of the ways Beets
tries to identify albums and songs is by examining filenames and paths.
If the music library is organized with top-level directories being artist
names, subdirectories being album names, and files within album folders
being songs from that album then Beets can use that structure to match
artists and albums with online data. Should your music library be organized
in a different fashion then Beets will still identify artists, albums, genres,
songs, and other metadata using intelligent matching algorithms.

The music library must be writeable by the MusicPlayerPlus user.

### Configure the music library location

If you have created a music library in a location other than `$HOME/Music/`
then edit `$HOME/.config/mpd/mpd.conf` and set the `music_directory`
configuration to the location of your music library.

After configuring `mpd.conf` with the proper `music_directory` setting,
run the command `mppinit sync`. This will update other MusicPlayerPlus
and Beets configuration files that need to know the music library location.

If your music library location is `$HOME/Music` then you can skip this step.

### Initializing the Beets media library management system

**[NOTE:]** Beets is NOT the now defunct music service purchased by Apple.
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

Try playing something with a command like:

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

**[NOTE:]** MusicPlayerPlus has configured the Beets play plugin
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

### Additional Beets metadata analysis and retrieval

After completing the Beets music library import with either `mppinit import`
or `mpplus -I`, additional Beets metadata can be retrieved with the command:

```
mppinit metadata
```

This will identify and delete duplicate tracks, retrieve album genres,
download album cover art, and optionally analyze and retrieve metadata
for all songs in the music library using the
[Essentia extractor](https://essentia.upf.edu/index.html) and
[Essentia trained models](https://essentia.upf.edu/models.html).

MusicPlayerPlus uses Essentia for extracting acoustic characteristics
of music, including low-level spectral information, rhythm, keys, scales,
and much more, and automatic annotation by genres, moods, and instrumentation.

This is the same sort of thing that
[AcousticBrainz](https://acousticbrainz.org/) does but the AcousticBrainz
project is no longer collecting data and will be withdrawn in 2023.
MusicPlayerPlus provides the same functionality using pre-compiled and
packaged Essentia binaries and models.

However, the process of analyzing, extracting, and retrieving metadata
can be time consuming for a large music library. The `mppinit metadata`
command performs several metadata retrieval steps in a non-interactive
manner and in the background so it can be left unattended if desired.

The individual metadata retrieval steps performed automatically by
`mppinit metadata` can be performed manually using the instructions
in the following sections.

#### Remove duplicate tracks

Duplicate tracks in the Beets library can be removed with the command:

```
beet duplicates -d
```

The '-d' option removes duplicate files from the music library location
on disk as well as removing duplicates in the Beets library. Omit the '-d'
option to remove duplicates in the Beets library only.

The Beets configuration file at `$HOME/.config/beets/config.yaml` has
been configured to use checksums to find duplicates. This can be a fairly
slow process for a large library. Beets can also find duplicates using
MusicBrainz IDs or other methods. MusicPlayerPlus prefers checksums but
if this process is too time consuming, it may be preferable to use IDs.

#### Rename tracks that were duplicates

After removing duplicates it is often the case that filenames contain
no longer needed characters (e.g. "Love Song 2.mp3" which was a duplicate
of "Love Song.mp3"). To correct these filenames, simply run `beet move`.

#### Retrieve genres from Last.fm

The Beets lastgenre plugin can be used to augment the genre metadata of
a Beets music library. The MusicPlayerPlus configuration of the lastgenre
Beets plugin includes a customized local copy of the genre tree and whitelist.
To retrieve genres using the Beets lastgenre plugin, run the command
`beet lastgenre`.

#### Analyze and extract additional metadata with Essentia

To analyze and extract a wealth of additional metadata directly from
all of the audio files in the music library, run the command `mpplus -X all`.
To limit the analysis and extraction to a subset of audio files in the
music library, run the command `mpplus -X [QUERY]` where 'QUERY' is a
[Beets query](https://beets.readthedocs.io/en/stable/reference/query.html).
For example, to analyze and extract metadata for all audio files
with beets-per-minute set to 0, run the command `mpplus -X bpm:0`.

The analysis and extraction of metadata with Essentia can be a time consuming
process. For this reason, it is run non-interactively in the background with
a terminal window being used to monitor the progress. The extraction
process can be left unattended and may need to run for hours. If the length
of time required to analyze and extract metadata using Essentia is
prohibitive then it may be preferable to use the Beets acousticbrainz plugin
to retrieve additional metadata. To use acousticbrainz, uncomment the
acousticbrainz entries in `$HOME/.config/beets/config.yaml` and run the
command `beet acousticbrainz [QUERY]`. Using the acousticbrainz plugin is
faster (the analysis has already been performed) but incomplete, often
incorrect, out-of-date, and will no longer be available in 2023.

### Convert WAV format media files

If your music library contains WAV format media files, these will not be
imported into Beets. The WAV format is an older media format and does not
support metadata in a way that Beets can manipulate. If you wish to import
these files into Beets it is necessary to convert them to a format that
is compatible with Beets. MusicPlayerPlus provides a convenience command
to convert all WAV format media to MP3 format.

Convert WAV format media files in your library to MP3 format files with
the command `mpplus -F`. Conversion from WAV to MP3 allows these files to
be imported into the Beets media library management system.

If the music libary does not contain any WAV format media files then this
step can be skipped.

### Import the music library into Beets

If you wish to manage your music library with Beets, import the music library
with the command `mpplus -I`.

To get started using the Beets media library management system, it is
necessary to import your music library into the Beets database. This process
catalogs your music collection and improves its metadata. The default
Beets configuration provided by MusicPlayerPlus moves and tags files in the
music library during this process. It adds music library data to the Beets
database. To import your music library into Beets, issue the following command:

```
mpplus -I
```

The Beets import defaults are controlled by the Beets configuration file
at `$HOME/.config/beets/config.yaml` and command-line options to the
`beet import` command. By default, MusicPlayerPlus imports the MPD music
library into Beets, moving rather than copying files to conform with
standard detected artist/album/song naming conventions, and writing
detected metadata. A log of the album import is written to the file
`$HOME/.config/beets/logs/import.log`. A log of the singletons import
is written to the file `$HOME/.config/beets/logs/import_singletons.log`.
A log of the import times is written to the file
`$HOME/.config/beets/logs/import_time.log`.

Prior to performing the intial Beets import of your music library,
examine the *import* section of the Beets configuration at
`$HOME/.config/beets/config.yaml`. Modify the *import* settings
to suit your preferences. The default *import* settings configured
by MusicPlayerPlus are:

```
import:
    copy: yes
    move: yes
    write: yes
    incremental: yes
    incremental_skip_later: yes
    quiet: no
    quiet_fallback: asis
    resume: yes
    from_scratch: no
    default_action: apply
    detail: yes
    non_rec_action: ask
    # duplicate_action can be 'skip', 'keep', 'remove', 'merge' or 'ask'
    duplicate_action: skip
    group_albums: no
    autotag: yes
    bell: no
    log: ~/.config/beets/logs/import.log
```

You may prefer to set `move: no` if you do not wish your files and folders
to be moved or if you wish that rearrangement to be performed by
copying rather than moving. Moving conserves disk space, copying preserves
a libary's structure but can consume much additional disk space. The
MusicPlayerPlus default preference is to move rather than copy.

**[NOTE:]** Some users prefer to use
[MusicBrainz Picard](https://picard.musicbrainz.org/)  to tag their music
library. If you have previously tagged your music library using
MusicBrainz Picard then you may wish to modify the default Beets
*import* configuration to preserve Picard tagging and speed up import.
An example *import* section of the Beets `config.yaml` that would
preserve Picard tags might look like the following:

```
import:
    write: no
    copy: no
    move: no
    resume: ask
    incremental: yes
    incremental_skip_later: no
    from_scratch: no
    timid: yes
    log: ~/.config/beets/logs/import.log
    group_albums: no
    autotag: yes
    bell: no
```

The import process, depending on the size of the music library and metadata
analyzed, may take several hours. For this reason, it is performed in the
background and non-interactively. For extremely large music libraries
(e.g. over 200GB) the import may need to run overnight. As long as your
computer remains on and connected to the Internet, the import process
should run uninterrupted and without need for attention. You may continue
working or leave the import unattended.

An interrupted Beets import can be resumed simply by re-running the
`mpplus -I` command. The import process will skip over previously imported
items and import items the previous import failed to reach.

A rough estimate of the time to import a music library into Beets can be
obtained by calculating the size of the library. On a moderately equipped
Ubuntu Linux system, a test import of an 11GB music library of over 500 songs
took about 10 minutes. Import times will vary with network speed, how quickly
metadata sources like MusicBrainz and Bandcamp can locate media matches,
and many other factors. Unfortunately, it is not possible to speed an
import beyond the frequency with which MusicBrainz permits API requests.

A very large music library of hundreds of Gigabytes and thousands of songs
will take hours to import. For this reason MusicPlayerPlus disables many
of the automatic retrieval of metadata and tagging during import that some
of the Beets plugins are capable of. This minimizes the import time. For
example, the auto fetching of cover art, lyrics, and genre during import
is disabled. These and other music library metadata retrieval can be
performed post-import using MusicPlayerPlus commands.

A good workflow might be: Kickoff a Beets import, Enjoy some Sun with a good
book, Check the import progress, Return to reading, Check progress, Repeat.

When running in the background, monitor the progess of the import by
examining the log file. For example, to view the progress of the album
import in real-time:

```
tail -f $HOME/.config/beets/logs/import_time.log
```

To view the progress of the singletons import in real-time:

```
tail -f $HOME/.config/beets/logs/import_singletons.log
```

The `mpplus -I ...` command performs both an import of the music library
albums and an import of singleton songs.

Music library folders that are skipped are likely those for which `beet import`
did not find the entire album. These songs will be picked up and imported
during the subsequent import where singletons are identified and imported.

If a manual beets import is desired, it may be performed by issuing the commands:

```
beet import -[w|W] <MUSIC_DIRECTORY>
```

and

```
beet import -[w|W] -s <MUSIC_DIRECTORY>
```

Where <MUSIC_DIRECTORY> is the full pathname to your music library and the
`-w` flag indicates 'write metadata' while `-W` flag indicates 'do not write metadata'.
Omitting both the `-w` and `-W` flags will use the *write* setting in the
*import* section of `~/.config/beets/config.yaml` to determin if metadata are
written. The first import command above imports albums from the music library
at <MUSIC_DIRECTORY>. The second import command imports singleton songs.

To perform a faster import without auto-tagging, writing tags, or copying,
run the command:

```
beet import -qAWC
```

If you wish to update the tags in your music library after having imported
without auto-tagging or writing, use the `mbsync` plugin to update tags
using MusicBrainz: `beet mbsync`.

If auto-tagging, writing, moving, or otherwise modifying the music library
during import, you may wish to backup your music library prior to importing.
To view help on Beets importing, run the command `beet help import`.

If new songs or albums are added to the MPD music library, the Beets import
can be re-run with `mpplus -I` or manually and only new albums and songs
will be added to the Beets database as the import is performed incrementally.
Incremental imports is a configuration option set in the *import* section
of the Beets `$HOME/.config/beets/config.yaml` configuration file.

List the currently imported music library items with the command `beet list`
and the currently imported music library albums with the command `beet list -a`.

View music library statistics with the `beet describe` command. For example,
to view library genre statistics run the command `beet describe genre`.
To view library beats per minute statistics run the command `beet describe bpm`.

The `beet` command-line reference is available at
https://beets.readthedocs.io/en/latest/reference/cli.html

Learn more about the Beets media library management system at
https://beets.io/

### Beets import followup steps

The Beets import process is very smart and able to detect most albums and
song titles. It uses an extensive database and several algorithms. But it
does fail to correctly identify some albums and songs. MusicPlayerPlus
has done quite a bit of work behind the scenes to make the Beets setup
process as simple as possible. The import process is run non-interactively
and in the background as is the metadata analysis and retrieval. For this
reason, the Beets import process has made intelligent choices for you
during import. These are almost always correct due to the algorithms used.

After completing a Beets import it is recommended to manually review the
resulting music library. If there are albums which Beets was not able to
identify then they will be in folders named something like:

```
$HOME/Music/John Doe/[0000] Unknown Album (6_19_2007 4_56_26 PM)
```

The Beet list command can be used to display a list of all albums or
tracks in the imported library. Run `beet ls -a` to list all albums
and `beet ls` to list all tracks. A summary of music library statistics
can be obtained with `beet stats`. Information on a particular item
or items can be obtained with `beet info -l [QUERY]` where `QUERY` is
a Beets query. An empty query returns the entire library. To view info
on a particular item, provide enough of the item filename or path to
identify it as the query. For example, to view info on the items in
the above unknown album by artist John Doe: `beet info -l 'John Doe'`.

Find and review all albums in the music library with folders containing
`Unknown Album` with the command `beet list -a 'Unknown Album'` or by
listing the folders in the music library itself with a command like
`ls -d "/path/to/music_library/*/*Unknown Album*"`.

Often a simple interactive re-import of these folders can be performed
to properly identify them. Using the above unknown album as an example,
to perform an interactive re-import of this unknown album:

```
beet import "$HOME/Music/John Doe/*Unknown Album*"
```

#### Performing an interactive Beets import

The interactive import process will provide a list of candidates to
select from, display the changes it would make, and ask to apply
those changes. If prompted, enter the number of the candidate best
matching the album you wish to identify and apply those changes when
subsequently prompted for your approval. If none of the candidates
displayed matches the album, display additional candidates or cancel
the import if no match can be found. The MusicBrainz database contains
information on roughly 1.9 million artists, 3 million releases, and 26.5
million recordings. But not everything. If one or more of the albums
in the music library cannot be identified by MusicBrainz or Beetcamp
(or Discogs if you have enabled that plugin) then it may need to be
updated manually.

Use the
[beet modify](https://beets.readthedocs.io/en/stable/reference/cli.html#modify)
command to selectively add titles, artists, track names, and other
metadata to items in the music library for which there is no match in
any of the configured metadata sources. For example, if the above unknown
album by John Doe is not matched by MusicBrainz or Beetcamp but you know
the album title is "Eldorado" then the `beet modify` command can be used
to set the album title for these items:

```
beet modify -a john doe unknown album 'album=Eldorado'
```

Provide enough of a query to uniquely identify the album or track(s) you wish
to modify. To verify that the query uniquely identifies the album in question,
prior to issuing the modify command, list it with

```
beet ls -a john doe unknown album
```

#### Performing a Beets import with a MusicBrainz ID

Another method of identifying an album or tracks is by searching the
MusicBrainz website, locating the release you have, and setting the
MusicBrainz ID for that release during import. There are several ways
to do this. Suppose you have a digital rip of the "Snow Crash" audio
book by Neil Stephenson on cassette tape. The non-interactive Beets
import will probably misidentify it as one of the more recent releases
of the audio book as the cassette release is lower in the candidate list.

To correct the non-interactive import or to import this audio book for
the first time, first visit the musicbrainz.org and search for "Snow Crash"
in Releases. Locate the cassette release of Snow Crash at
https://musicbrainz.org/release/d5f4b4eb-0b58-4886-872b-d538863941dc

The long string of digits and letters in the URL is the MusicBrainz ID
for this release. Copy that string. Perform an interactive Beets import
of the Snow Crash audio book digital media in the music library:

```
beet import "$HOME/Music/Neil Stephenson/Snow Crash"
```

At the Beets import prompt:

```
Enter search, enter Id, aBort, eDit, edit Candidates, plaY?
```

Enter 'I' to "enter Id". At the following prompt for ID enter the
MusicBrainz ID copied earlier from the URL of the release followed
at the next prompt with 'A' to Apply these changes.

Manual modification of the Beets music library should be needed infrequently
unless the library contains unreleased, unpublished, or otherwise
unavailable digital audio recordings.

After manually identifying and updating an album or track that MusicBrainz
could not match, it is possible to update the MusicBrainz database with
that new information. Beets even has a
[MusicBrainz Submit Plugin](https://beets.readthedocs.io/en/stable/plugins/mbsubmit.html)
to ease this process but that is beyond the scope of this document.

Generally, an interactive Beets re-import of unmatched, miscategorized
or misnamed items in the music library is all that is needed.

### Download album cover art with the mpplus command

Once your music library has been created and the library location set,
you can download album cover art with the command `mpplus -D`.

This step is optional as album cover art is not required by either Beets
or MusicPlayerPlus. However, cover art can be displayed by many MPD clients
and enhances the user experience. Pre-existing album cover art is retained
and only albums with no cover art are updated.

Note, for large libraries with many albums missing cover art this process
may take a long time. Monitor the download process with the command
`tail -f ${HOME}/.config/mpcplus/download_art.log`.

The `mpplus -D` command downloads album cover art for each album in your
music library and places the album cover art in the file `cover.jpg` in the
album folder. The `mpplus -D` command downloads images of size 600x600.

If you wish to name album cover art differently or if you wish to create
a different sized album cover art, then execute the `sacad_r` command
directly rather than with `mpplus -D` as follows:


```
sacad_r <MUSIC_DIRECTORY> <SIZE> <FILENAME>
```

Where <MUSIC_DIRECTORY> is the full pathname to your music library, <SIZE>
is the desired size of the image, and <FILENAME> is the desired filename.

For example, to download album art for a music library located in
`/u/audio/music` with an image size of 500x500, in PNG image format,
and album art filenames `album_cover.png` execute the command:

```
sacad_r /u/audio/music 500 album_cover.png
```

Learn more about the Smart Automatic Cover Art Downloader `sacad` at
https://github.com/desbma/sacad

### Downloading album cover art with the fetchart Beets plugin

MusicPlayerPlus includes the `fetchart` Beets plugin. This plugin is
pre-installed, pre-configured, and enabled. The fetchart Beets plugin
can be used as an alternative method of downloading album cover art and
provides significant flexibility and options not available to `sacad`.

Our experience here at MusicPlayerPlus labs has found that `mpplus -D` finds
and downloads a higher number of album cover art than the fetchart plugin.
The fetchart plugin is useful for augmenting an initial cover art download
with `mpplus -D`. The fetchart plugin also has many configurable options
allowing the user to specify download parameters and sources. The choice
of which method to use to download cover art is left to the user, both
methods being supported and useful.

The fetchart plugin can also be used to selectively download album cover
art by specifying a Beets query limiting the download to those albums
that do not already have album cover art. This can be useful as a way
to augment a previous cover art download with `mpplus -D`.

To identify albums without cover art, issue the command:

```
/usr/share/musicplayerplus/scripts/find-no-covers.sh
```

After identifying music library folders without album cover art using the
above command, the `fetchart` Beets plugin, can be used to download cover
art for those albums with no cover art by specifying a Beets query. For
example, if the artist "John Doe" has no album cover art, issue the command:

```
beet fetchart 'John Doe'
```

## Playlist creation

MusicPlayerPlus has configured the `smartplaylist` Beets plugin to create
several MPD playlists automatically. In addition to these smart playlists
which get automatically created and updated when the music library changes,
MusicPlayerPlus includes the `create_playlist` command. This command can
be used to generate new playlists based on Beets queries. Any valid Beets
query can be supplied as a command-line argument and all songs matching
the query will be added to a newly created playlist.

```
Usage: create_playlist [-n playlist-name] [-q beets-query] [-ou]
Where:
	-n 'playlist-name' specifies the playlist name
	-q 'beets-query' specifies the Beets query to use
        multiple '-q query' arguments may be provided
	-o indicates overwrite any pre-existing playlist of same name
	-u displays this usage message and exits
```

For example, to create a playlist named "LoveList" of all songs in the
music library with "love" in the song title, artist name, or album name,
issue the command `create_playlist -n LoveList -q love`. To create a
playlist named "Dance Party" with all songs whose metadata attributes
include both "danceable" and "party" values, issue the command:

```
create_playlist -n "Dance Party" -q mood_party:party -q danceable:danceable
```

**[NOTE:]** The flexible tags that Essentia adds based on the acoustic
analysis it performs are interesting but not necessarily accurate. Tags
like *gender*, *danceable*, *mood_party*, and others reflect an aspect
of the acoustic profile but may not reflect the tag name. For example,
the *gender* tag can have the value *male* or *female* but it does not
mean that the vocalist is actually male or female, just that the acoustics
in the song are more that of a male or female. Many of the songs by
progressive rock band "Uriah Heep" are tagged as *gender:female*
because the vocalist for that band, a male, has a high pitched voice.
Think of these flexible tags based on acoustic analysis as representing
various aspects of the acoustics rather than strictly how they are named.

## Fetching lyrics

The Beets media library management system can fetch lyrics using the
`lyrics` plugin. The MusicPlayerPlus default Beets configuration does
not enable lyrics fetching using the `lyrics` plugin during Beets import.
Albums and songs imported using Bandcamp as a metadata source will
automatically fetch lyrics during import. That is, the default MusicPlayerPlus
Beets import will only fetch lyrics for Bandcamp sourced items.

To view a list of music library items that do not have lyrics metadata,
issue the command:

```
beet list -f '$artist: $album - $title' lyrics::^$
```

To fetch lyrics for all songs in the music library that do not already have
lyrics. after the Beets import process completes issue the command:

```
mpplus -L
```

MusicPlayerPlus has chosen to provide a default Beets configuration that
disables auto-fetching of lyrics during import in order to reduce the
import time which can be quite lengthy. To enable auto-fetching of lyrics
during import, prior to performing the music library Beets import, change
the `auto: no` setting to `auto: yes` in the `lyrics:` section of
`$HOME/.config/beets/config.yaml`

The `lyrics` plugin also has a configuration option to specify the lyrics
sources to query when fetching lyrics. Some of these online lyrics services
have blocked the Beets User-Agent thereby disabling those services for
Beets users. Google does not block Beets lyrics queries but the Google
lyrics service requires additional configuration - providing an API key.

For these reasons, MusicPlayerPlus distributes a Beets lyrics configuration
that auto-fetches from Bandcamp when that is used as a metadata source
and only queries the Polish lyrics service at https://www.tekstowo.pl
for `lyrics` plugin requests. You may wish to add to or replace this service.
To modify the list of lyrics services queried by the Beets `lyrics` plugin,
change the `sources: tekstowo` setting in the `lyrics:` section of
`$HOME/.config/beets/config.yaml` to one or more of
`google musixmatch genius tekstowo`.

See the
[Beets lyrics plugin documentation](https://beets.readthedocs.io/en/stable/plugins/lyrics.html)
for more information on configuring and using the Beets lyrics plugin.

## Finding duplicate tracks

The Beets `duplicates` plugin can be used to identify duplicate tracks
in the music library. Why and how I ended up with so many duplicate tracks
in my library is a mystery but Beets helped me find and delete them, saving
quite a bit of disk space and confusion. MusicPlayerPlus includes a default
configuration for the duplicates plugin that uses checksums to identify
duplicate files in the music library. The duplicates plugin has several
methods available including comparing MusicBrainz IDs, any checksum program
you wish to configure, and any set of attributes you prefer to use.

MusicPlayerPlus utilizes checksums calculated by `ffmpeg` as the preferred
method for detecting duplicates. Edit the `duplicates` configuration section
of `$HOME/.config/beets/config.yaml` to enable an alternate method.

In addition to configuring the method for identifying duplicates, you may
wish to modify how the duplicates plugin decides which of the duplicates
to keep and which to delete. By default, the tie-breaking procedure favors
the most complete metadata attribute set. If you would like to consider the
lower bitrates as duplicates, set `tiebreak: items: [bitrate]` in the
duplicates section of the Beets `config.yaml`.

The recommended workflow for identifying and removing duplicate tracks from
a music library consists of two passes. First, simply list any duplicates
with the command `beet duplicates`. Review these files manually to confirm
they are not wanted. The listing of duplicates in the first pass made no
changes to the music library. To delete the duplicates from the Beets
library and from disk, run a second pass with the command `beet duplicates -d`.

After deleting duplicates, some filenames may have an inappropriate suffix
that was added when they were initially created. For example, there may
have been duplicate files `Some Artist/Some Album/Some Track.mp3` and
`Some Artist/Some Album/Some Track.2.mp3`. The duplicates plugin may
have deleted `Some Artist/Some Album/Some Track.mp3` and left
`Some Artist/Some Album/Some Track.2.mp3` in the library. To rename these
kinds of files use the `beet move` command. Again, recommended workflow
is two passes. First perform a dry-run with the command `beet move -p`.
This will tell you what it would do but not do anything. If that looks
good then perform the file renaming with the command `beet move`.

## Automated audio analysis and audio-based information retrieval

MusicPlayerPlus includes a pre-compiled `essentia_streaming_extractor_music`
binary along with pre-installed and configured `xtractor` Beets plugin.
This enables Beets to analyze audio files, extract information on a wide
variety of audio parameters, and write metadata to the Beets library.
This process can provide information on audio in a music library that
can be used to filter and select songs by their detected audio qualities.

**[NOTE on acousticbrainz]** The `acousticbrainz` plugin performs a
similar function and even uses the same Essentia technology to analyze
audio data. However, `acousticbrainz` does not perform an analysis on
all songs and, worse, the AcousticBrainz service is being retired in 2023.
For these reasons, MusicPlayerPlus provides the built-in capability
to perform acoustic audio analysis using Essentia and the xtractor plugin.

To perform an audio analysis and audio-based information retrieval using
MusicPlayerPlus, issue the command `mpplus -X 'query'` where 'query' is
a Beets media library query specifying which songs or albums or artists
to match. A special query of 'all' indicates the entire music library.

For example, to analyze and retrieve audio information on all songs with
filename or pathname that include the string "Love Party", issue the command:

```
mpplus -X 'love party'
```

To analyze and retrieve audio information on the entire music library:

```
mpplus -X all
```

The process of analyzing and retrieving audio information can be very
time consuming. For this reason, the process is run in the background
and a terminal window is opened to monitor the extraction process.

Due to the long extraction times needed to perform an audio analysis,
it is often desirable to identify only those songs that do not already
have the desired metadata and perform the analysis selectively on those
songs using an appropriate Beets query string. For example, to identify
all songs in the music library that do not have a 'mood_party' metadata
tag, issue the command:

```
beet list -f '$artist: $album - $title' mood_party::^$
```

Other songs for which the `xtractor` plugin may prove useful are those
for which `acousticbrainz` mistakenly added a bpm value of 0 or those
for which no bpm attribute has been set. To find songs with a bpm value
of 0, issue the command:

```
beet list -f '$artist: $album - $title' bpm:0
```

To find songs for which no bpm attribute has been set, issue the command:

```
beet list -f '$artist: $album - $title' bpm::^$
```

To analyze and retrieve information for all songs in the music library
with a bpm value of 0 or no bpm attribute, issue the command:

```
mpplus -X bpm:0 bpm::^$
```

If audio analysis and extraction of metadata on a large music library is
too time consuming then it may be preferable to use the `acousticbrainz`
plugin to download metadata from MusicBrainz followed by selective use
of the Beets xtractor plugin. Using `acousticbrainz` is faster because
no audio analysis is needed, the MusicBrainz database already has the
metadata for songs recognized by their MusicBrainz ID. Unfortunately,
the MusicBrainz metadata is not always correct and the AcousticBrainz
service is being retired. But until that day (sometime in 2023) it may
be preferable to enable the `acousticbrainz` Beets plugin and perform
a two-pass metadata update of the music library:

- Uncomment the acousticbrainz plugin in `$HOME/.config/beets/config.yaml`
- Run `beet acousticbrainz`
- Repair those songs for which acousticbrainz set bpm to 0
    - `beet xt bpm:0`

This two-pass solution will not repair all of the mistakes that AcousticBrainz
has made, only the beets-per-minute metadata, but it is a lot faster than
a full analysis and extraction using `beet xt`.

It is preferable to perform the time consuming full analysis and extraction
using `beet xt` or `mpplus -X all` as this will extract metadata with a much
higher accuracy and it will continue to be supported after AcousticBrainz is
no longer available.

### MusicPlayerPlus custom xtractor metadata configuration

The default MusicPlayerPlus Beets configuration includes a customized
`xtractor` plugin configuration providing many flexible metadata tags.
These include metadata tags for Beets per Minute, Key and Scale,
Replay Gain, Integrated Loudness, Loudness Range, Timbre, Danceability,
and Moods. The metadata names for these custom flexible tags are

- *bpm*
- *danceability*
- *beats_count*
- *average_loudness*
- *initial_key*
- *key_key*
- *key_scale*
- *chords_key*
- *chords_scale*
- *replay_gain*
- *integrated_loudness*
- *loudness_range*
- *timbre*
- *danceable*
- *genre_rosamerica*
- *is_danceable*
- *mood_acoustic*
- *mood_aggressive*
- *mood_electronic*
- *mood_happy*
- *mood_sad*
- *mood_party*
- *mood_relaxed*

If the music library has been analyzed with Essentia using the xtractor
plugin (e.g. `mpplus -X all` or `mppinit metadata`) then these custom tags
can be used in Beets queries.

For example, to list all songs which have been tagged as being in the key of G:

```
beet list key_key:G key_scale:major
```

To list all songs in the key of G minor:

```
beet list key_key:G key_scale:minor
```

The customized entry for these metadata targets in the xtractor section
of the Beets configuration `$HOME/.config/beets/config.yaml` is:

```
    low_level_targets:
      bpm:
        path: "rhythm.bpm"
        type: integer
        required: yes
      danceability:
        path: "rhythm.danceability"
        type: float
      beats_count:
        path: "rhythm.beats_count"
        type: integer
      average_loudness:
        path: "lowlevel.average_loudness"
        type: float
        required: yes
      initial_key:
        path: "tonal.initial_key"
        type: string
    high_level_targets:
      key_key:
        path: "tonal.key_edma.key"
        type: string
      key_scale:
        path: "tonal.key_edma.scale"
        type: string
      chords_key:
        path: "tonal.chords_key"
        type: string
      chords_scale:
        path: "tonal.chords_scale"
        type: string
      replay_gain:
        path: "metadata.audio_properties.replay_gain"
        type: float
      integrated_loudness:
        path: "lowlevel.loudness_ebu128.integrated"
        type: float
      loudness_range:
        path: "lowlevel.loudness_ebu128.loudness_range"
        type: float
      timbre:
        path: "highlevel.timbre.value"
        type: string
        required: yes
      danceable:
        path: "highlevel.danceability.value"
        type: string
        required: yes
      is_danceable:
        path: "highlevel.danceability.all.danceable"
        type: float
      genre_rosamerica:
        path: "highlevel.genre_rosamerica.value"
        type: string
      mood_acoustic:
        path: "highlevel.mood_acoustic.value"
        type: string
        required: yes
      mood_aggressive:
        path: "highlevel.mood_aggressive.value"
        type: string
        required: yes
      mood_electronic:
        path: "highlevel.mood_electronic.value"
        type: string
        required: yes
      mood_happy:
        path: "highlevel.mood_happy.value"
        type: string
        required: yes
      mood_sad:
        path: "highlevel.mood_sad.value"
        type: string
        required: yes
      mood_party:
        path: "highlevel.mood_party.value"
        type: string
        required: yes
      mood_relaxed:
        path: "highlevel.mood_relaxed.value"
        type: string
        required: yes
```

The MusicPlayerPlus Beets xtractor plugin configuration can be modified to
suit the use case. However, if the xtractor has been run prior to modifying
its configuration, it may be necessary to re-analyze the digital audio in
order to update the metadata to reflect the revised configuration. To force
re-analysis and metadata update using the xtractor plugin, use the `-f` flag:

```
beet xtractor -f -w [QUERY]
```

Previously analyzed xtractro output files are stored in
`$HOME/.config/beets/xtraction_data/` as JSON format files named either by
the audio's MusicBrainz track ID or a randomly generated UUID.

To manually examine the acoustic properties calculated using Essentia
of a particular song, identify that song's MusicBrainz track ID then look
for the JSON file with that ID in the above directory. To identify a
song's MusicBrainz track ID, use a Beets query that uniquely identifies the
song in a command like:

```
beet info -l [QUERY] | grep mb_trackid
```

### MusicPlayerPlus acousticbrainz metadata configuration

MusicPlayerPlus supports two different methods for retrieving audio-based
track metadata. The previous section described the configuration of the
Beets Xtractor plugin which utilizes Essentia to analyze and retrieve
audio-based information. The Xtractor process can be extremely time
consuming, especially for large music libraries, as it entails a complex
analysis of each audio track. For this reason, an alternative method
of retrieving audio-based information is provided.

The Beets `acousticbrainz` plugin can be used to query the AcousticBrainz
database and retrieve already analyzed audio-based information for tracks
in that database. This process is much faster than the Xtractro process
as the analysis has previously been performed by the AcousticBrainz service.

If the music library metadata has been updated using the acousticbrainz
plugin (e.g. `mpplus -x all` or `mppinit -a metadata`) then these custom
tags can be used in Beets queries.

- *average_loudness*
- *bpm*
- *chords_changes_rate*
- *chords_key*
- *chords_number_rate*
- *chords_scale*
- *danceable*
- *gender*
- *genre_rosamerica*
- *initial_key*
- *key_strength*
- *mood_acoustic*
- *mood_aggressive*
- *mood_electronic*
- *mood_happy*
- *mood_party*
- *mood_relaxed*
- *mood_sad*
- *moods_mirex*
- *rhythm*
- *timbre*
- *tonal*
- *voice_instrumental*

Unfortunately, the AcousticBrainz service is deprecated, no longer updated,
and will be disabled in 2023. Further, it does not provide accurate
information on some metadata. Locally analyzed acoustic information using
Essentia is of higher quality and reliable. The AcousticBrainz service provides
lower quality information and is not reliable. However, the significant
advantage to using AcousticBrainz is the overhead in time is much much
lower than that with the Xtractor plugin.

## Configuring the Discogs metadata source

Beets uses [MusicBrainz](https://musicbrainz.org) as the default source
for metadata. This is sufficient for many Beets users as MusicBrainz has
a vast amount of data and requires no registration or API key to utilize.
However, MusicBrainz does not have every artist, album, and song in its
database and there are several Beets plugins that extend metadata search
to additional sources.

MusicPlayerPlus provides a pre-configured Beets `bandcamp` plugin to enable
[Bandcamp](https://bandcamp.com) as a metadata source. Many artists have
chosen to only distribute their works on Bandcamp in order to avoid the
miniscule royalty payments made to artists by streaming services. Bandcamp
is also a frequent home for artists who have not been signed to a label
or are otherwise not well known. The default Beets configuration that
MusicPlayerPlus provides will automatically use Bandcamp as a metadata
source thereby finding matches for artists, albums, and songs in the music
library that were downloaded from Bandcamp.

The default MusicPlayerPlus Beets configuration, using both MusicBrainz
and Bandcamp as metadata sources, should satisfy most use cases.
However, some users may wish to enable additional metadata sources.
One of the most complete sources of music metadata is
[Discogs](https://www.discogs.com). To enable Discogs as a metadata source,
it will be necessary to register for a Discogs account, provide
authorization and credentials, and configure the `discogs` plugin.
This process is not too difficult but MusicPlayerPlus cannot perform
this automatically. It must be performed by the Beets user. Follow these
steps to enable Discogs as a metadata source:

* Register for a free Discogs account by visiting https://www.discogs.com
* No need to install `python3-discogs-client` as this was done during the MusicPlayerPlus initialization with `mppinit`
* Login to Discogs to generate a user token
    * Visit the [Developer settings page](https://www.discogs.com/settings/developers) at https://www.discogs.com/settings/developers
    * Press the `Generate new token` button
    * Copy the generated token to your clipboard (select the token and press Ctrl-c)
* Add the generated token in the `discogs` section of the Beets configuration
    * Edit `$HOME/.config/beets/config.yaml`
    * Uncomment the `discogs` entry in the `plugins` section
    * Uncomment the `discogs:` plugin configuration section
    * Set the `user_token:` configuration option in the `discogs:` section
        * user_token: Your_Discogs_User_Token

After editing `config.yaml` the discogs plugin configuration should look
something like the following:

```yaml
discogs:
    source_weight: 0.0
    index_tracks: yes
    user_token: DruiHPid_I_Just_Made_This_Up_LSAPTWUCnpRJ
```

After completing the above steps Discogs will be used as a metadata
source by Beets. The `user_token` setting will alleviate the need to
authenticate or provide credentials when accessing Discogs with Beets.

For additional information on the Beets discogs plugin, visit
https://beets.readthedocs.io/en/stable/plugins/discogs.html

## MusicPlayerPlus Beets plugins

Beets includes an extensive set of plugins that can be used to enhance and
extend the functionality of the media library management Beets provides. Many
Beets plugins are installed and configured automatically by MusicPlayerPlus.

MusicPlayerPlus 2.0.1 and later include automated installation and
configuration for the following Beets plugins:

* acousticbrainz, albumtypes, bandcamp, describe, duplicates, edit
* extrafiles, fetchart, fromfilename, hook, importadded, info, lyrics
* lastgenre, missing, mbsync, mpdstats, play, playlist, smartplaylist
* mpdupdate, unimported, xtractor, yearfixer

See the MusicPlayerPlus [Wiki article on Beets plugins](https://github.com/doctorfree/MusicPlayerPlus/wiki/BeetsPlugins)
for an introduction to the installed and configured MusicPlayerPlus Beets plugins.

## See also

- [MusicPlayerPlus](../projects/MusicPlayerPlus.md)
