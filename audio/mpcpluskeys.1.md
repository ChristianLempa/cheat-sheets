---
title: MPCPLUSKEYS
section: 1
header: User Manual
footer: mpcpluskeys 0.10
date: March 24, 2022
---
## NAME
**mpcpluskeys** - mpcplus key bindings and usage

## DESCRIPTION
This man page describes the key bindings used to control
the **mpcplus** music player client.

## KEYS - CUSTOM

The following custom *mpcplus* key bindings are provided:

-   `[ Alt-c ]` - Display album cover art for currently playing song
-   `[ Alt-f ]` - Open the fuzzy finder to search/select media
-   `[ Alt-m ]` - Open the MPD monitor in a terminal window
-   `[ Alt-r ]` - Raise/lower the spectrum visualizer window

## KEYS - MOVEMENT

-   `[ Up k ]` - Move cursor up
-   `[ Down j ]` - Move cursor down
-   `[ [ ]` - Move cursor up one album
-   `[ ] ]` - Move cursor down one album
-   `[ { ]` - Move cursor up one artist
-   `[ } ]` - Move cursor down one artist
-   `[ Page Up ]` - Page up
-   `[ Page Down ]` - Page down
-   `[ Home ]` - Home
-   `[ End ]` - End
-   `[ Tab ]` - Switch to next screen in sequence
-   `[ Shift-Tab ]` - Switch to previous screen
-   `[ F1 ]` - Show help
-   `[ 1 ]` - Show playlist
-   `[ 2 ]` - Show browser
-   `[ 3 ]` - Show search engine
-   `[ 4 ]` - Show media library
-   `[ 5 ]` - Show playlist editor
-   `[ 6 ]` - Show tag editor
-   `[ 7 ]` - Show outputs
-   `[ 8 ]` - Show music visualizer
-   `[ = ]` - Show clock
-   `[ @ ]` - Show server info

## KEYS - GLOBAL

-   `[ s ]` - Stop
-   `[ p ]` - Pause
-   `[ > ]` - Next track
-   `[ < ]` - Previous track
-   `[ Ctrl-H Backspace ]` - Replay playing song
-   `[ f ]` - Seek forward in playing song
-   `[ b ]` - Seek backward in playing song
-   `[ - Left ]` - Decrease volume by 2%
-   `[ Right + ]` - Increase volume by 2%
-   `[ t ]` - Toggle space mode (select/add)
-   `[ T ]` - Toggle add mode (add or remove/always add)
-   `[ | ]` - Toggle mouse support
-   `[ v ]` - Reverse selection
-   `[ V ]` - Remove selection
-   `[ B ]` - Select songs of album around the cursor
-   `[ a ]` - Add selected items to playlist
-   ``[ ` ]`` - Add random items to playlist
-   `[ r ]` - Toggle repeat mode
-   `[ z ]` - Toggle random mode
-   `[ y ]` - Toggle single mode
-   `[ R ]` - Toggle consume mode
-   `[ Y ]` - Toggle replay gain mode
-   `[ # ]` - Toggle bitrate visibility
-   `[ Z ]` - Shuffle playlist
-   `[ x ]` - Toggle crossfade mode
-   `[ X ]` - Set crossfade
-   `[ u ]` - Start music database update
-   `[ : ]` - Execute command
-   `[ Ctrl-F ]` - Apply filter
-   `[ / ]` - Find item forward
-   `[ ? ]` - Find item backward
-   `[ , ]` - Jump to previous found item
-   `[ . ]` - Jump to next found item
-   `[ w ]` - Toggle find mode (normal/wrapped)
-   `[ G ]` - Locate song in browser
-   `[ ~ ]` - Locate song in media library
-   `[ Ctrl-L ]` - Lock/unlock current screen
-   `[ Left h ]` - Switch to master screen (left one)
-   `[ Right l ]` - Switch to slave screen (right one)
-   `[ E ]` - Locate song in tag editor
-   `[ P ]` - Toggle display mode
-   `[ \ ]` - Toggle user interface
-   `[ ! ]` - Toggle displaying separators between albums
-   `[ g ]` - Jump to given position in playing song (formats: mm:ss,
    x%)
-   `[ i ]` - Show song info
-   `[ I ]` - Show artist info
-   `[ L ]` - Toggle lyrics fetcher
-   `[ F ]` - Toggle fetching lyrics for playing songs in background
-   `[ q ]` - Quit

## KEYS - PLAYLIST

-   `[ Enter ]` - Play selected item
-   `[ Delete ]` - Delete selected item(s) from playlist
-   `[ c ]` - Clear playlist
-   `[ C ]` - Clear playlist except selected item(s)
-   `[ Ctrl-P ]` - Set priority of selected items
-   `[ Ctrl-K m ]` - Move selected item(s) up
-   `[ n Ctrl-J ]` - Move selected item(s) down
-   `[ M ]` - Move selected item(s) to cursor position
-   `[ A ]` - Add item to playlist
-   `[ e ]` - Edit song
-   `[ S ]` - Save playlist
-   `[ Ctrl-V ]` - Sort playlist
-   `[ Ctrl-R ]` - Reverse playlist
-   `[ o ]` - Jump to current song
-   `[ U ]` - Toggle playing song centering

## KEYS - BROWSER

-   `[ Enter ]` - Enter directory/Add item to playlist and play it
-   `[ Space ]` - Add item to playlist/select it
-   `[ e ]` - Edit song
-   `[ e ]` - Edit directory name
-   `[ e ]` - Edit playlist name
-   `[ 2 ]` - Browse MPD database/local filesystem
-   ``[ ` ]`` - Toggle sort mode
-   `[ o ]` - Locate playing song
-   `[ Ctrl-H Backspace ]` - Jump to parent directory
-   `[ Delete ]` - Delete selected items from disk
-   `[ G ]` - Jump to playlist editor (playlists only)

## KEYS - SEARCH ENGINE

-   `[ Enter ]` - Add item to playlist and play it/change option
-   `[ Space ]` - Add item to playlist
-   `[ e ]` - Edit song
-   `[ y ]` - Start searching
-   `[ 3 ]` - Reset search constraints and clear results

## KEYS - MEDIA LIBRARY

-   `[ 4 ]` - Switch between two/three columns mode
-   `[ Left h ]` - Previous column
-   `[ Right l ]` - Next column
-   `[ Enter ]` - Add item to playlist and play it
-   `[ Space ]` - Add item to playlist
-   `[ e ]` - Edit song
-   `[ e ]` - Edit tag (left column)/album (middle/right column)
-   ``[ ` ]`` - Toggle type of tag used in left column
-   `[ m ]` - Toggle sort mode

## KEYS - PLAYLIST EDITOR

-   `[ Left h ]` - Previous column
-   `[ Right l ]` - Next column
-   `[ Enter ]` - Add item to playlist and play it
-   `[ Space ]` - Add item to playlist/select it
-   `[ e ]` - Edit song
-   `[ e ]` - Edit playlist name
-   `[ Ctrl-K m ]` - Move selected item(s) up
-   `[ n Ctrl-J ]` - Move selected item(s) down
-   `[ Delete ]` - Delete selected playlists (left column)
-   `[ Delete ]` - Delete selected item(s) from playlist (right column)
-   `[ c ]` - Clear playlist
-   `[ C ]` - Clear playlist except selected item(s)
-   `[ Ctrl-P ]` - Set priority of selected items
-   `[ Ctrl-K m ]` - Move selected item(s) up
-   `[ n Ctrl-J ]` - Move selected item(s) down
-   `[ M ]` - Move selected item(s) to cursor position
-   `[ A ]` - Add item to playlist
-   `[ e ]` - Edit song
-   `[ S ]` - Save playlist
-   `[ Ctrl-V ]` - Sort playlist
-   `[ Ctrl-R ]` - Reverse playlist
-   `[ o ]` - Jump to current song
-   `[ U ]` - Toggle playing song centering

## KEYS - LYRICS

-   `[ Space ]` - Toggle reloading lyrics upon song change
-   `[ e ]` - Open lyrics in external editor
-   ``[ ` ]`` - Refetch lyrics

## KEYS - TERMINAL WINDOWS

-   `[ Alt-f ]` - Open the fuzzy finder to search/select media
-   `[ Alt-m ]` - Open the MPD monitor in a terminal window
-   `[ Alt-r ]` - Raise/lower the spectrum visualizer window

## KEYS - TMUX SESSIONS

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

## KEYS - TINY TAG EDITOR

-   `[ Enter ]` - Edit tag
-   `[ y ]` - Save

## KEYS - TAG EDITOR

-   `[ Enter ]` - Edit tag/filename of selected item (left column)
-   `[ Enter ]` - Perform operation on all/selected items (middle
    column)
-   `[ Space ]` - Switch to albums/directories view (left column)
-   `[ Space ]` - Select item (right column)
-   `[ Left h ]` - Previous column
-   `[ Right l ]` - Next column
-   `[ Ctrl-H Backspace ]` - Jump to parent directory (left column,
    directories view)

## LICENSING
MPCPLUSKEYS is distributed under an Open Source license.
See the file COPYING in the MPCPLUSKEYS source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPCPLUSKEYS and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/mpcplus/issues

## SEE ALSO
**mpcplus**(1), **mpplus**(1), **mpd**(1)

Full documentation and sources at:

https://github.com/doctorfree/mpcplus

