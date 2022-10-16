---
title: MPCPLUS
section: 1
header: User Manual
footer: mpcplus 0.10
date: March 24, 2022
---
## NAME
**mpcplus** - An ncurses Music Player Daemon (MPD) client

## SYNOPSIS
**mpcplus** [options]

## DESCRIPTION
*mpcplus* is an NCurses client for MPD (Music Player Daemon), inspired by
ncmpcpp and configured to integrate with `mppcava`, a customized fork of the
Cava spectrum visualizer.

Read more about MPD at http://www.musicpd.org

Read more about `mppcava` at
https://github.com/doctorfree/MusicPlayerPlus/tree/master/mppcava#readme

## COMMAND LINE OPTIONS
Mandatory arguments to long options are mandatory for short options as well.

* **-h**, **--host**=_HOST_  
  Connect to server at host [localhost]
* **-p**, **--port**=_PORT_  
  Connect to server at port [6600]
* **--current-song**[=_FORMAT_]  
  Print current song using given format and exit
* **-c**, **--config**=_FILE_  
  Specify configuration file(s)
* **--ignore-config-errors**  
  Ignore unknown and invalid options in configuration files
* **-b**, **--bindings**=_FILE_  
  Specify bindings file(s)
* **-s**, **--screen &lt;name&gt;**  
  Specify the startup screen (&lt;name&gt; may be: help, playlist, browser, search_engine, media_library, playlist_editor, tag_editor, outputs, visualizer, clock)
* **-S**, **--slave-screen &lt;name&gt;**  
  Specify the startup slave screen (&lt;name&gt; may be: help, playlist, browser, search_engine, media_library, playlist_editor, tag_editor, outputs, visualizer, clock)
* **-q**, **--quiet**  
  Suppress logs and excess output
* **-?**, **--help**  
  Display help.
* **-v**, **--version**  
  Display version information.
  

## CONFIGURATION

When mpcplus starts, it tries to read settings from
$XDG_CONFIG_HOME/mpcplus/config and $HOME/.mpcplus/config files. If no
configuration is found, mpcplus uses its default configuration. An example
configuration file containing all default values is provided and can be found in
[/usr/share/mpcplus/config](https://github.com/doctorfree/mpcplus/blob/master/doc/config)

Note: Configuration option values can either be enclosed in quotation marks or not.
 - If they are enclosed, the leftmost and the rightmost quotation marks are treated as delimiters, therefore it is not necessary to escape quotation marks you use within the value itself.
 - If they are not, any whitespace characters between = and the first printable character of the value, as well as whitespace characters after the last printable character of the value are trimmed.

Therefore the rule of thumb is: if you need whitespaces at the beginning or at the end of the value, enclose it in quotation marks. Otherwise, don't.

Note: COLOR has to be the name (not a number) of one of colors 1-8 from SONG FORMAT section.

Supported configuration options:

* **mpcplus_directory = PATH**  
  Directory for storing mpcplus related files. Changing it is useful if you want to store everything somewhere else and provide command line setting for alternative location to config file which defines that while launching mpcplus.
* **lyrics_directory = PATH**  
  Directory for storing downloaded lyrics. It defaults to ~/.lyrics since other MPD clients (eg. ncmpcpp) also use that location.
* **mpd_host = HOST**  
  Connect to MPD running on specified host/unix socket. When HOST starts with a '/', it is assumed to be a unix socket. Note: MPD_HOST environment variable overrides this setting.
* **mpd_port = PORT**  
  Connect to MPD on the specified port. Note: MPD_PORT environment variable overrides this setting.
* **mpd_password = PASSWORD**  
  Use PASSWORD to authenticate to MPD.
* **mpd_music_dir = PATH**  
  Search for files in specified directory. This is needed for tag editor to work.
* **mpd_connection_timeout = SECONDS**  
  Set connection timeout to MPD to given value.
* **mpd_crossfade_time = SECONDS**  
  Default number of seconds to crossfade, if enabled by mpcplus.
* **visualizer_data_source = LOCATION**  
  Source of data for the visualizer. For MPD it's going to be a fifo output, for
  Mopidy a udpsink output (see the example configuration file for more details).
* **visualizer_output_name = NAME**  
  Name of output that provides data for visualizer. Needed to keep sound and visualization in sync.
* **visualizer_in_stereo = yes/no**  
  Should be set to 'yes', if fifo output's format was set to 44100:16:2.
* **visualizer_type = spectrum/wave/wave_filled/ellipse**  
  Defines default visualizer type (spectrum is available only if mpcplus was compiled with fftw support).
* **visualizer_look = STRING**  
  Defines visualizer's look (string has to be exactly 2 characters long: first one is for wave whereas second for frequency spectrum).
* **visualizer_color = COLORS**  
  Comma separated list of colors to be used in music visualization.
* **visualizer_fps = FPS**  
  The amount of frames per second for the visualizer.
* **visualizer_autoscale = yes/no**  
  Automatically scale visualizer size.
* **visualizer_spectrum_smooth_look = yes/no**  
  For spectrum visualizer, use unicode block characters for a smoother, more continuous look. This will override the visualizer_look option. With transparent terminals and visualizer_in_stereo set, artifacts may be visible on the bottom half of the visualization.
* **visualizer_spectrum_dft_size = NUMBER**  
  For spectrum visualizer, a value between 1 and 5 inclusive. Specifying a larger value makes the visualizer look at a larger slice of time, which results in less jumpy visualizer output.
* **visualizer_spectrum_gain = dB**  
  Gain for spectrum visualizer in dB, larger/smaller values shift bars up/down.
* **visualizer_spectrum_hz_min = Hz**  
  For spectrum visualizer, left-most frequency of visualizer, must be less than HZ MAX.
* **visualizer_spectrum_hz_max = Hz**  
  For spectrum visualizer, right-most frequency of visualizer, must be greater than HZ MIN.
* **system_encoding = ENCODING**  
  If you use encoding other than utf8, set it in order to handle utf8 encoded strings properly.
* **playlist_disable_highlight_delay = SECONDS**  
  Delay for highlighting playlist since the last key was pressed. If set to 0, highlighting never fades away.
* **message_delay_time = SECONDS**  
  Delay for displayed messages to remain visible.
* **song_list_format**  
  Song format for lists of songs.
* **song_status_format**  
  Song format for statusbar.
* **song_library_format**  
  Song format for media library.
* **alternative_header_first_line_format = TEXT**  
  Now playing song format for the first line in alternative user interface header window.
* **alternative_header_second_line_format = TEXT**  
  Now playing song format for the second line in alternative user interface header window.
* **current_item_prefix = TEXT**  
  Prefix for currently selected item.
* **current_item_suffix = TEXT**  
  Suffix for currently selected item.
* **current_item_inactive_column_prefix = TEXT**  
  Prefix for currently selected item in the inactive column.
* **current_item_inactive_column_suffix = TEXT**  
  Suffix for currently selected item in the inactive column.
* **now_playing_prefix = TEXT**  
  Prefix for currently playing song.
* **now_playing_suffix = TEXT**  
  Suffix for currently playing song.
* **browser_playlist_prefix = TEXT**  
  Prefix for playlists in Browser.
* **selected_item_prefix = TEXT**  
  Prefix for selected items.
* **selected_item_suffix = TEXT**  
  Suffix for selected items.
* **modified_item_prefix = TEXT**  
  Prefix for modified item (tag editor).
* **browser_sort_mode**  
  Determines sort mode for browser. Possible values are "type", "name", "mtime", "format" and "none".
* **browser_sort_format**  
  Format to use for sorting songs in browser. For this option to be effective, browser_sort_mode must be set to "format".
* **song_window_title_format**  
  Song format for window title.
* **song_columns_list_format**  
  Format for songs' list displayed in columns.
* **execute_on_song_change = COMMAND**  
  Shell command to execute on song change.
* **execute_on_player_state_change = COMMAND**  
  Shell command to execute on player state change. The environment variable
  **MPD_PLAYER_STATE**
  is set to the current state (either unknown, play, pause, or stop) for its duration.
* **playlist_show_mpd_host = yes/no**  
  If enabled, current MPD host will be shown in playlist.
* **playlist_show_remaining_time = yes/no**  
  If enabled, time remaining to end of playlist will be shown after playlist statistics.
* **playlist_shorten_total_times = yes/no**  
  If enabled, total/remaining playlist time displayed in statusbar will be shown using shortened units' names (d:h:m:s instead of days:hours:minutes:seconds).
* **playlist_separate_albums = yes/no**  
  If enabled, separators will be placed between albums.
* **playlist_display_mode = classic/columns**  
  Default display mode for Playlist.
* **browser_display_mode = classic/columns**  
  Default display mode for Browser.
* **search_engine_display_mode = classic/columns**  
  Default display mode for Search engine.
* **playlist_editor_display_mode = classic/columns**  
  Default display mode for Playlist editor.
* **discard_colors_if_item_is_selected = yes/no**  
  Indicates whether custom colors of tags have to be discarded if item is selected or not.
* **show_duplicate_tags = yes/no**  
  Indicates whether mpcplus should display multiple tags as-is or remove duplicates.
* **incremental_seeking = yes/no**  
  If enabled, seek time will increment by one each second of seeking.
* **seek_time = SECONDS**  
  Base seek time to begin with.
* **volume_change_step = NUMBER**  
  Number of percents volume has to be increased/decreased by in volume_up/volume_down.
* **autocenter_mode = yes/no**  
  Default state for autocenter mode at start.
* **centered_cursor = yes/no**  
  If enabled, currently highlighted position in the list will be always centered.
* **progressbar_look = TEXT**  
  This variable defines the look of progressbar. Note that it has to be exactly two or three characters long.
* **default_place_to_search_in = database/playlist**  
  If set to "playlist", Search engine will perform searching in current MPD playlist rather than in music database.
* **user_interface = classic/alternative**  
  Default user interface used by mpcplus at start.
* **data_fetching_delay = yes/no**  
  If enabled, there will be a 250ms delay between refreshing position in media library or playlist editor and fetching appropriate data from MPD. This limits data fetched from the server and is particularly useful if mpcplus is connected to a remote host.
* **media_library_primary_tag = artist/album_artist/date/genre/composer/performer**  
  Default tag type for leftmost column in media library.
* **media_library_albums_split_by_date = yes/no**  
  Determines whether albums in media library should be split by date.
* **media_library_hide_album_dates = yes/no**  
  Determines whether album dates in media library should be hidden.
* **default_find_mode = wrapped/normal**  
  If set to "wrapped", going from last found position to next will take you to the first one (same goes for the first position and going to previous one), otherwise no actions will be performed.
* **default_tag_editor_pattern = TEXT**  
  Default pattern used by Tag editor's parser.
* **header_visibility = yes/no**  
  If enabled, header window will be displayed, otherwise hidden.
* **statusbar_visibility = yes/no**  
  If enabled, statusbar will be displayed, otherwise hidden.
* **connected_message_on_startup = yes/no**  
  Show the "Connected to ..." message on startup
* **titles_visibility = yes/no**  
  If enabled, column titles will be displayed, otherwise hidden.
* **header_text_scrolling = yes/no**  
  If enabled, text in header window will scroll if its length is longer then actual screen width, otherwise it won't.
* **cyclic_scrolling = yes/no**  
  If enabled, cyclic scrolling is used (e.g. if you press down arrow being at the end of list, it'll take you to the beginning)
* **lyrics_fetchers = FETCHERS**  
  Comma separated list of lyrics fetchers.
* **follow_now_playing_lyrics = yes/no**  
  If enabled, lyrics will be switched at song's change to currently playing one's (Note: this works only if you are viewing lyrics of item from Playlist).
* **fetch_lyrics_for_current_song_in_background = yes/no**  
  If enabled, each time song changes lyrics fetcher will be automatically run in background in attempt to download lyrics for currently playing song.
* **store_lyrics_in_song_dir = yes/no**  
  If enabled, lyrics will be saved in song's directory, otherwise in ~/.lyrics. Note that it needs properly set mpd_music_dir.
* **generate_win32_compatible_filenames = yes/no**  
  If set to yes, filenames generated by mpcplus (with tag editor, for lyrics, artists etc.) will not contain the following characters: \\?\*:|
* **allow_for_physical_item_deletion = yes/no**  
  If set to yes, it will be possible to physically delete files and directories from the disk in the browser.
* **lastfm_preferred_language = ISO 639 alpha-2 language code**  
  If set, mpcplus will try to get info from last.fm in language you set and if it fails, it will fall back to English. Otherwise it will use English the first time.
* **space_add_mode = add_remove/always_add**  
  If set to add_remove, attempting to add files that are already in playlist will remove them. Otherwise they can be added multiple times.
* **show_hidden_files_in_local_browser = yes/no**  
  Trigger for displaying in local browser files and directories that begin with '.'
* **screen_switcher_mode = SWITCHER_MODE**  
  If set to "previous", key_screen_switcher will switch between current and last used screen. If set to "screen1,...screenN" (a list of screens) it will switch between them in a sequence. Syntax clarification can be found in example config file.
* **startup_screen = SCREEN_NAME**  
  Screen that has to be displayed at start (playlist by default).
* **startup_slave_screen = SCREEN_NAME**  
  Slave screen that has to be displayed at start (nothing by default).
* **startup_slave_screen_focus = yes/no**  
  If set to yes, slave screen will be the active one after startup. Otherwise master screen will be.
* **locked_screen_width_part = 20-80**  
  If you want to lock a screen, mpcplus asks for % of locked screen's width to be reserved before that and provides a default value, which is the one you can set here.
* **ask_for_locked_screen_width_part = yes/no**  
  If enabled, mpcplus will ask for % of locked screen's width each time you want to lock a screen. If you disable that, it'll silently attempt to use default value.
* **media_library_column_width_ratio_two = a:b**  
  The ratio of the column widths in the media library, when there are two columns.
* **media_library_column_width_ratio_three = a:b:c**  
  The ratio of the column widths in the media library, when there are three columns.
* **playlist_editor_column_width_ratio = a:b**  
  The ratio of the column widths in the playlist editor.
* **jump_to_now_playing_song_at_start = yes/no**  
  If enabled, mpcplus will jump at start to now playing song if mpd is playing or paused.
* **ask_before_clearing_playlists = yes/no**  
  If enabled, user will be asked if he really wants to clear the playlist after pressing key responsible for that.
* **clock_display_seconds = yes/no**  
  If enabled, clock will display time in format hh:mm:ss, otherwise hh:mm.
* **display_volume_level = yes/no**  
  If enabled, volume level will be displayed in statusbar, otherwise not.
* **display_bitrate = yes/no**  
  If enabled, bitrate of currently playing song will be displayed in statusbar.
* **display_remaining_time = yes/no**  
  If enabled, remaining time of currently playing song will be be displayed in statusbar instead of elapsed time.
* **regular_expressions = none/basic/extended/perl**  
  Type of currently used regular expressions.
* **ignore_leading_the = yes/no**  
  If enabled, word "the" at the beginning of tags/filenames/sort format will be ignored while sorting items.
* **ignore_diacritics = yes/no**  
  If enabled, diacritics in strings will be ignored while searching and filtering lists.
* **block_search_constraints_change_if_items_found = yes/no**  
  If enabled, fields in Search engine above "Reset" button will be blocked after successful searching, otherwise they won't.
* **mouse_support = yes/no**  
  If set to yes, mouse support will be enabled.
* **mouse_list_scroll_whole_page = yes/no**  
  If enabled, mouse wheel will scroll the whole page of item list at a time, otherwise the number of lines specified by lines_scrolled variable.
* **lines_scrolled = NUMBER**  
  Number of lines that are scrolled with mouse wheel.
* **empty_tag_marker = TEXT**  
  Text that will be displayed, if requested tag is not set.
* **tags_separator = TEXT**  
  Separator that is placed between tags. Also interpreted by tag editor which splits input string into separate tags using it.
* **tag_editor_extended_numeration = yes/no**  
  If enabled, tag editor will number tracks using format xx/yy (where xx is the current track and yy is total amount of all numbered tracks), not plain xx.
* **media_library_sort_by_mtime = yes/no**  
  If enabled, media library will be sorted by modification time. Otherwise lexicographic sorting is used.
* **enable_window_title = yes/no**  
  If enabled, mpcplus will override current window title with its own one.
* **search_engine_default_search_mode = MODE_NUMBER**  
  Number of default mode used in search engine.
* **external_editor = PATH**  
  Path to external editor used to edit lyrics.
* **use_console_editor = yes/no**  
  If your external editor is console application, you need to enable it.
* **colors_enabled = yes/no**  
  No need to describe it, huh?
* **empty_tag_color = COLOR**  
  Color of empty tag marker.
* **header_window_color = COLOR**  
  Color of header window.
* **volume_color = COLOR**  
  Color of volume state.
* **state_line_color = COLOR**  
  Color of lines separating header and statusbar from main window.
* **state_flags_color = COLOR**  
  Color of MPD status flags.
* **main_window_color = COLOR**  
  Color of main window.
* **color1 = COLOR**  
  One of colors used in Song info, Tiny tag editor and Search engine.
* **color2 = COLOR**  
  One of colors used in Song info, Tiny tag editor and Search engine.
* **progressbar_color = COLOR**  
  Color of progressbar.
* **progressbar_elapsed_color = COLOR**  
  Color of part of progressbar that represents elapsed time.
* **statusbar_color = COLOR**  
  Color of statusbar.
* **statusbar_time_color = COLOR**  
  Color of current track time shown in statusbar.
* **player_state_color = COLOR**  
  Color of player state shown in statusbar.
* **alternative_ui_separator_color = COLOR**  
  Color of separators used in alternative user interface.
* **window_border_color = BORDER**  
  Border color of pop-up windows. If set to 'none', no border will be shown.
* **active_window_border = COLOR**  
  Color of active window's border.

## BINDINGS

When mpcplus starts, it tries to read bindings from
$XDG_CONFIG_HOME/mpcplus/bindings and ~/.mpcplus/bindings files. If no bindings
file is found, mpcplus uses the defaults. An example bindings file with default
values can be found in
[/usr/share/mpcplus/mpcplus-cheat-sheet.md](https://github.com/doctorfree/mpcplus/tree/master/share/mpcplus-cheat-sheet.md)

Mpcplus includes bindings to integrate with `mppcava`, a customized fork of
the Cava spectrum visualizer. By default, these bindings are Alt-0 through
Alt-9 to set the transparency of the terminal window in which mpcplus is running.
Alt-1 sets the window to 90% transparent, Alt-2 to 80% and so on Alt-9 to 10%
transparent, and Alt-0 to 100% opaque. These transparency setting bindings are
useful when running `mpcplus` and `mppcava` in separate overlapping windows,
the spectrum visualizer visible through and behind the mpcplus window.

Alt-f opens a terminal window running the fuzzy media finder `fzmp`.

Alt-r raises/lowers the spectrum visualizer window.

You can view current keybindings by pressing F1.

## SONG FORMAT

For song format you can use:

 %l - length
 %f - filename
 %D - directory
 %a - artist
 %A - album artist
 %t - title
 %b - album
 %y - date
 %n - track number (01/12 -&gt; 01)
 %N - full track info (01/12 -&gt; 01/12)
 %g - genre
 %c - composer
 %p - performer
 %d - disc
 %C - comment
 %P - priority
 $R - begin right alignment

You can also put them in { } and then they will be displayed only if all requested values are available and/or define alternate value with { }|{ } e.g. {%a - %t}|{%f} will check if artist and title tags are available and if they are, display them. Otherwise it'll display filename.

**Note**: If you want to set limit on maximal length of a tag, just put the appropriate number between % and character that defines tag type, e.g. to make album take max. 20 terminal cells, use '%20b'.

**Note**: Format that is similar to "%a - %t" (i.e. without any additional braces) is equal to "{%a - %t}", so if one of the tags is missing, you'll get nothing.

Text can have different color than the main window, e.g. if you want length to be green, write $3%l$9.

Available values for colors:

 - 0 - default window color (discards all other colors)
 - 1 - black
 - 2 - red
 - 3 - green
 - 4 - yellow
 - 5 - blue
 - 6 - magenta
 - 7 - cyan
 - 8 - white
 - 9 - end of current color

**Note**: colors can be nested, so if you write $2some$5text$9,
it'll disable only usage of blue color and make red the current one.

## LICENSING
MPCPLUS is distributed under an Open Source license.
See the file COPYING in the MPCPLUS source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPCPLUS and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/mpcplus/issues

## NOTE

Since MPD uses UTF-8, mpcplus needs to convert characters to the charset used by the local system. If you get character conversion errors while you are running mpcplus, you probably need to set up your locale. This is done by setting LANG and LC_ALL/LC_CTYPE environment variables (LC_CTYPE only affects character handling).

## HOMEPAGE

-&gt; https://github.com/doctorfree/mpcplus

## SEE ALSO
**mpcpluskeys**(1), **mpc**(1), **mpd**(1), **mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/mpcplus

