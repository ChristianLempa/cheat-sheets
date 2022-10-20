---
tags:
    - audio
    - mpd
    - client
    - terminal
    - character
    - mpplus
categories:
    - audio
---

# ncmpcpp – featureful NCurses based MPD client

[![License: GPL v2](https://img.shields.io/badge/License-GPL_v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

An mpd client (compatible with mopidy) with a UI very similar to ncmpc, but it provides new useful features such as support for regular expressions for library searches, extended song format, items filtering, the ability to sort playlists, and a local filesystem browser.

The [mpcplus](mpcplus.md) fork of ***ncmpcpp*** is used by [MusicPlayerPlus](../projects/MusicPlayerPlus.md) as the default MPD client.

## configure ncmpcpp

```shell
mkdir ~/.ncmpcpp
cat <<EOF > ~/.ncmpcpp/config
ncmpcpp_directory =         "~/.ncmpcpp"
mpd_host =                  "127.0.0.1"
mpd_port =                  "6600"
mpd_music_dir =             "/var/lib/mpd/music/"
EOF
```

## Movement

```text
    Up k               Move cursor up
    Down j             Move cursor down
    [                  Move cursor up one album
    ]                  Move cursor down one album
    {                  Move cursor up one artist
    }                  Move cursor down one artist
    Page Up            Page up
    Page Down          Page down
    Home               Home
    End                End
    Tab                Switch to next screen in sequence
    Shift-Tab          Switch to previous screen in sequence
    F1                 Show help
    1                  Show playlist
    2                  Show browser
    3                  Show search engine
    4                  Show media library
    5                  Show playlist editor
    6                  Show tag editor
    7                  Show outputs
    8                  Show music visualizer
    =                  Show clock
    @                  Show server info
```

## Global

```text
    s                  Stop
    p                  Pause
    >                  Next track
    <                  Previous track
    Ctrl-H Backspace   Replay playing song
    f                  Seek forward in playing song
    b                  Seek backward in playing song
    - Left             Decrease volume by 2%
    Right +            Increase volume by 2%
    t                  Toggle space mode (select/add)
    T                  Toggle add mode (add or remove/always add)
    |                  Toggle mouse support
    v                  Reverse selection
    V                  Remove selection
    B                  Select songs of album around the cursor
    a                  Add selected items to playlist
    `                  Add random items to playlist
    r                  Toggle repeat mode
    z                  Toggle random mode
    y                  Toggle single mode
    R                  Toggle consume mode
    Y                  Toggle replay gain mode
    #                  Toggle bitrate visibility
    Z                  Shuffle playlist
    x                  Toggle crossfade mode
    X                  Set crossfade
    u                  Start music database update
    :                  Execute command
    Ctrl-F             Apply filter
    /                  Find item forward
    ?                  Find item backward
    ,                  Jump to previous found item
    .                  Jump to next found item
    w                  Toggle find mode (normal/wrapped)
    G                  Locate song in browser
    ~                  Locate song in media library
    Ctrl-L             Lock/unlock current screen
    Left h             Switch to master screen (left one)
    Right l            Switch to slave screen (right one)
    E                  Locate song in tag editor
    P                  Toggle display mode
    \                  Toggle user interface
    !                  Toggle displaying separators between albums
    g                  Jump to given position in playing song (formats: mm:ss, x%)
    i                  Show song info
    I                  Show artist info
    L                  Toggle lyrics fetcher
    F                  Toggle fetching lyrics for playing songs in background
    q                  Quit
```

## Playlist

```text
    Enter              Play selected item
    Delete             Delete selected item(s) from playlist
    c                  Clear playlist
    C                  Clear playlist except selected item(s)
    Ctrl-P             Set priority of selected items
    Ctrl-K m           Move selected item(s) up
    n Ctrl-J           Move selected item(s) down
    M                  Move selected item(s) to cursor position
    A                  Add item to playlist
    e                  Edit song
    S                  Save playlist
    Ctrl-V             Sort playlist
    Ctrl-R             Reverse playlist
    o                  Jump to current song
    U                  Toggle playing song centering
```

## Browser

```text
    Enter              Enter directory/Add item to playlist and play it
    Space              Add item to playlist/select it
    e                  Edit song/directory/playlist name
    2                  Browse MPD database/local filesystem
    `                  Toggle sort mode
    o                  Locate playing song
    Ctrl-H Backspace   Jump to parent directory
    Delete             Delete selected items from disk
    G                  Jump to playlist editor (playlists only)
```

## Search engine

```text
    Enter              Add item to playlist and play it/change option
    Space              Add item to playlist
    e                  Edit song
    y                  Start searching
    3                  Reset search constraints and clear results
```

## Media library

```text
    4                  Switch between two/three columns mode
    Left h             Previous column
    Right l            Next column
    Enter              Add item to playlist and play it
    Space              Add item to playlist
    e                  Edit song
    e                  Edit tag (left column)/album (middle/right column)
    `                  Toggle type of tag used in left column
    m                  Toggle sort mode
```

## Playlist editor

```text
    Left h             Previous column
    Right l            Next column
    Enter              Add item to playlist and play it
    Space              Add item to playlist/select it
    e                  Edit song/playlist name
    Ctrl-K m           Move selected item(s) up
    n Ctrl-J           Move selected item(s) down
    Delete             Delete selected playlists (left column)
    C                  Clear playlist except selected item(s)
    Ctrl-P             Set priority of selected items
    Ctrl-K m           Move selected item(s) up
    n Ctrl-J           Move selected item(s) down
    M                  Move selected item(s) to cursor position
    A                  Add item to playlist
    S                  Save playlist
    Ctrl-V             Sort playlist
    Ctrl-R             Reverse playlist
    o                  Jump to current song
    U                  Toggle playing song centering
```

## Search engine

```text
    Enter              Add item to playlist and play it/change option
    Space              Add item to playlist
    e                  Edit song
    y                  Start searching
    3                  Reset search constraints and clear results
```

## Media library

```text
    4                  Switch between two/three columns mode
    Left h             Previous column
    Right l            Next column
    Enter              Add item to playlist and play it
    Space              Add item to playlist
    e                  Edit song/tag (left column)/album (middle/right column)
    `                  Toggle type of tag used in left column
    m                  Toggle sort mode
```

## Lyrics

```text
    Space              Toggle reloading lyrics upon song change
    e                  Open lyrics in external editor
    `                  Refetch lyrics
```

## Tiny tag editor

```text
    Enter              Edit tag
    y                  Save
```

## Tag editor

```text
    Enter              Edit tag/filename of selected item (left column)
    Enter              Perform operation on all/selected items (middle column)
    Space              Switch to albums/directories view (left column)
    Space              Select item (right column)
    Left h             Previous column
    Right l            Next column
    Ctrl-H Backspace   Jump to parent directory (left column, directories view)
```

## See also

- [mpcplus](mpcplus.md)
- [mpcplus.1](mpcplus.1.md)
- [mpcpluskeys.1](mpcpluskeys.1.md)
- [MusicPlayerPlus](../projects/MusicPlayerPlus.md)
