---
title: SCDL
section: 1
header: User Manual
footer: scdl 2.7.2
date: July 24, 2022
---
## NAME
scdl - Download tracks and albums from a Soundcloud account favorites

## SYNOPSIS
**scdl** (-l <track_url> | me) [-a | -f | -C | -t | -p | -r][-c | --force-metadata] [-n <maxtracks>][-o <offset>][--hidewarnings][--debug | --error][--path <path>] [--addtofile][--addtimestamp][--onlymp3][--hide-progress][--min-size <size>] [--max-size <size>][--remove][--no-album-tag][--no-playlist-folder] [--download-archive <file>][--sync <file>][--extract-artist][--flac][--original-art] [--original-name][--no-original][--only-original][--name-format <format>] [--strict-playlist][--playlist-name-format <format>][--client-id <id>] [--auth-token <token>][--overwrite][--no-playlist]
    
**scdl** -h | --help

**scdl** --version

## OPTIONS

- **-h --help**                       Show this screen
- **--version**                       Show version
- **-l [url]**                        URL can be track/playlist/user
- **-n [maxtracks]**                  Download the n last tracks of a playlist according to the creation date
- **-s**                              Download the stream of a user (token needed)
- **-a**                              Download all tracks of user (including reposts)
- **-t**                              Download all uploads of a user (no reposts)
- **-f**                              Download all favorites of a user
- **-C**                              Download all commented by a user
- **-p**                              Download all playlists of a user
- **-r**                              Download all reposts of user
- **-c**                              Continue if a downloaded file already exists
- **--force-metadata**                This will set metadata on already downloaded track
- **-o [offset]**                     Begin with a custom offset
- **--addtimestamp**                  Add track creation timestamp to filename, which allows for chronological sorting
- **--addtofile**                     Add artist to filename if missing
- **--debug**                         Set log level to DEBUG
- **--download-archive [file]**       Keep track of track IDs in an archive file, and skip already-downloaded files
- **--error**                         Set log level to ERROR
- **--extract-artist**                Set artist tag from title instead of username
- **--hide-progress**                 Hide the wget progress bar
- **--hidewarnings**                  Hide Warnings. (use with precaution)
- **--max-size [max-size]**           Skip tracks larger than size (k/m/g)
- **--min-size [min-size]**           Skip tracks smaller than size (k/m/g)
- **--no-playlist-folder**            Download playlist tracks into main directory, instead of making a playlist subfolder
- **--onlymp3**                       Download only the streamable mp3 file, even if track has a Downloadable file
- **--path [path]**                   Use a custom path for downloaded files
- **--remove**                        Remove any files not downloaded from execution
- **--sync [file]**                   Compares an archive file to a playlist and downloads/removes any changed tracks
- **--flac**                          Convert original files to .flac
- **--no-album-tag**                  On some player track get the same cover art if from the same album, this prevent it
- **--original-art**                  Download original cover art
- **--original-name**                 Do not change name of original file downloads
- **--no-original**                   Do not download original file; only mp3 or m4a
- **--only-original**                 Only download songs with original file available
- **--name-format [format]**          Specify the downloaded file name format
- **--playlist-name-format [format]** Specify the downloaded file name format, if it is being downloaded as part of a playlist
- **--client-id [id]**                Specify the client_id to use
- **--auth-token [token]**            Specify the auth token to use
- **--overwrite**                     Overwrite file if it already exists
- **--strict-playlist**               Abort playlist downloading if one track fails to download
- **--no-playlist**                   Skip downloading playlists

## DESCRIPTION

The *scdl* command can be used to download favorite tracks and albums from a users's Soundcloud account. MusicPlayerPlus provides a convenience wrapper for *scdl*, the script `/usr/share/musicplayerplus/scripts/soundcloud-download`.

## AUTHORS

*scdl* written by:

- @FlyinGrub https://github.com/flyingrub
- David Fischer @davidfischer-ch
- @7x11x13

*soundcloud-download* written by Ronald Record github@ronrecord.com

## LICENSING
SCDL is distributed under an Open Source license.
See the file LICENSE in the SCDL source distribution
for information on terms &amp; conditions for accessing and
otherwise using SCDL and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**bandcamp-dl**(1), **beet**(1), **mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

