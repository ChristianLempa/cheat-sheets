---
title: BEETSCONFIG
section: 5
header: User Manual
footer: beets 1.6.0
date: July 12, 2022
---
## NAME
beetsconfig - Beets media library management system configuration

## DESCRIPTION

Beets has an extensive configuration system that lets you customize
nearly every aspect of its operation. To configure beets, you create a
file called `config.yaml`. The location of the file depend on your
platform (type `beet config -p` to see the path on your system):

-   On Unix-like OSes, write `~/.config/beets/config.yaml`.
-   On Windows, use `%APPDATA%\beets\config.yaml`. This is usually in a
    directory like `C:\Users\You\AppData\Roaming`.
-   On OS X, you can use either the Unix location or
    `~/Library/Application Support/beets/config.yaml`.

You can launch your text editor to create or update your configuration
by typing `beet config -e`. (See the `config-cmd`
command for details.) It is also possible to customize the
location of the configuration file and even use multiple layers of
configuration. See [Configuration Location](#configuration-location),
below.

The config file uses [YAML](https://yaml.org/) syntax. You can use the
full power of YAML, but most configuration options are simple key/value
pairs. This means your config file will look like this:

    option: value
    another_option: foo
    bigger_option:
        key: value
        foo: bar

In YAML, you will need to use spaces (not tabs!) to indent some lines.
If you have questions about more sophisticated syntax, take a look at
the [YAML](https://yaml.org/) documentation.

The rest of this page enumerates the dizzying litany of configuration
options available in beets. You might also want to see an
`example <config-example>`.

## Global Options

These options control beets\' global operation.

### library

Path to the beets library file. By default, beets will use a file called
`library.db` alongside your configuration file.

### directory

The directory to which files will be copied/moved when adding them to
the library. Defaults to a folder called `Music` in your home directory.

### plugins

A space-separated list of plugin module names to load. See
`using-plugins`.

### include

A space-separated list of extra configuration files to include.
Filenames are relative to the directory containing `config.yaml`.

### pluginpath

Directories to search for plugins. Each Python file or directory in a
plugin path represents a plugin and should define a subclass of
`BeetsPlugin`. A plugin can then be
loaded by adding the filename to the [plugins]
configuration. The plugin path can either be a single string or a list
of strings\-\--so, if you have multiple paths, format them as a YAML
list like so:

    pluginpath:
        - /path/one
        - /path/two

### ignore

A list of glob patterns specifying file and directory names to be
ignored when importing. By default, this consists of `.*`, `*~`,
`System Volume Information`, `lost+found` (i.e., beets ignores
Unix-style hidden files, backup files, and directories that appears at
the root of some Linux and Windows filesystems).

### ignore_hidden

Either `yes` or `no`; whether to ignore hidden files when importing. On
Windows, the \"Hidden\" property of files is used to detect whether or
not a file is hidden. On OS X, the file\'s \"IsHidden\" flag is used to
detect whether or not a file is hidden. On both OS X and other platforms
(excluding Windows), files (and directories) starting with a dot are
detected as hidden files.

### replace

A set of regular expression/replacement pairs to be applied to all
filenames created by beets. Typically, these replacements are used to
avoid confusing problems or errors with the filesystem (for example,
leading dots, which hide files on Unix, and trailing whitespace, which
is illegal on Windows). To override these substitutions, specify a
mapping from regular expression to replacement strings. For example,
`[xy]: z` will make beets replace all instances of the characters `x` or
`y` with the character `z`.

If you do change this value, be certain that you include at least enough
substitutions to avoid causing errors on your operating system. Here are
the default substitutions used by beets, which are sufficient to avoid
unexpected behavior on all popular platforms:

    replace:
        '[\\/]': _
        '^\.': _
        '[\x00-\x1f]': _
        '[<>:"\?\*\|]': _
        '\.$': _
        '\s+$': ''
        '^\s+': ''
        '^-': _

These substitutions remove forward and back slashes, leading dots, and
control characters---all of which is a good idea on any OS. The fourth
line removes the Windows \"reserved characters\" (useful even on Unix
for for compatibility with Windows-influenced network filesystems like
Samba). Trailing dots and trailing whitespace, which can cause problems
on Windows clients, are also removed.

When replacements other than the defaults are used, it is possible that
they will increase the length of the path. In the scenario where this
leads to a conflict with the maximum filename length, the default
replacements will be used to resolve the conflict and beets will display
a warning.

Note that paths might contain special characters such as typographical
quotes (`“”`). With the configuration above, those will not be replaced
as they don\'t match the typewriter quote (`"`). To also strip these
special characters, you can either add them to the replacement list or
use the `asciify-paths` configuration
option below.

### path_sep_replace

A string that replaces the path separator (for example, the forward
slash `/` on Linux and MacOS, and the backward slash `\\` on Windows)
when generating filenames with beets. This option is related to
`replace`, but is distict from it for
technical reasons.

Changing this option is potentially dangerous. For example, setting it
to the actual path separator could create directories in unexpected
locations. Use caution when changing it and always try it out on a small
number of files before applying it to your whole library.

Default: `_`.

### asciify_paths

Convert all non-ASCII characters in paths to ASCII equivalents.

For example, if your path template for singletons is `singletons/$title`
and the title of a track is \"Café\", then the track will be saved as
`singletons/Cafe.mp3`. The changes take place before applying the
`replace` configuration and are roughly
equivalent to wrapping all your path templates in the `%asciify{}`
`template function <template-functions>`.

This uses the [unidecode module](https://pypi.org/project/Unidecode)
which is language agnostic, so some characters may be transliterated
from a different language than expected. For example, Japanese kanji
will usually use their Chinese readings.

Default: `no`.

### art_filename

When importing album art, the name of the file (without extension) where
the cover art image should be placed. This is a template string, so you
can use any of the syntax available to
`/reference/pathformat`. Defaults to
`cover` (i.e., images will be named `cover.jpg` or `cover.png` and
placed in the album\'s directory).

### threaded

Either `yes` or `no`, indicating whether the autotagger should use
multiple threads. This makes things substantially faster by overlapping
work: for example, it can copy files for one album in parallel with
looking up data in MusicBrainz for a different album. You may want to
disable this when debugging problems with the autotagger. Defaults to
`yes`.

### format_item[]

Format to use when listing *individual items* with the
`list-cmd` command and other commands that
need to print out items. Defaults to `$artist - $album - $title`. The
`-f` command-line option overrides this setting.

It used to be named [list_format_item].

### format_album[]

Format to use when listing *albums* with `list-cmd`
and other commands. Defaults to `$albumartist - $album`. The
`-f` command-line option overrides this setting.

It used to be named [list_format_album].

### sort_item

Default sort order to use when fetching items from the database.
Defaults to `artist+ album+ disc+ track+`. Explicit sort orders override
this default.

### sort_album

Default sort order to use when fetching albums from the database.
Defaults to `albumartist+ album+`. Explicit sort orders override this
default.

### sort_case_insensitive

Either `yes` or `no`, indicating whether the case should be ignored when
sorting lexicographic fields. When set to `no`, lower-case values will
be placed after upper-case values (e.g., *Bar Qux foo*), while `yes`
would result in the more expected *Bar foo Qux*. Default: `yes`.

### original_date

Either `yes` or `no`, indicating whether matched albums should have
their `year`, `month`, and `day` fields set to the release date of the
*original* version of an album rather than the selected version of the
release. That is, if this option is turned on, then `year` will always
equal `original_year` and so on. Default: `no`.

### artist_credit

Either `yes` or `no`, indicating whether matched tracks and albums
should use the artist credit, rather than the artist. That is, if this
option is turned on, then `artist` will contain the artist as credited
on the release.

### per_disc_numbering

A boolean controlling the track numbering style on multi-disc releases.
By default (`per_disc_numbering: no`), tracks are numbered per-release,
so the first track on the second disc has track number N+1 where N is
the number of tracks on the first disc. If this `per_disc_numbering` is
enabled, then the first (non-pregap) track on each disc always has track
number 1.

If you enable `per_disc_numbering`, you will likely want to change your
`path-format-config` also to include
`$disc` before `$track` to make filenames sort correctly in album
directories. For example, you might want to use a path format like this:

    paths:
        default: $albumartist/$album%aunique{}/$disc-$track $title

When this option is off (the default), even \"pregap\" hidden tracks are
numbered from one, not zero, so other track numbers may appear to be
bumped up by one. When it is on, the pregap track for each disc can be
numbered zero.

### aunique

These options are used to generate a string that is guaranteed to be
unique among all albums in the library who share the same set of keys.

The defaults look like this:

    aunique:
        keys: albumartist album
        disambiguators: albumtype year label catalognum albumdisambig releasegroupdisambig
        bracket: '[]'

See `aunique` for more details.

### terminal_encoding

The text encoding, as [known to
Python](https://docs.python.org/2/library/codecs.html#standard-encodings),
to use for messages printed to the standard output. It\'s also used to
read messages from the standard input. By default, this is determined
automatically from the locale environment variables.

### clutter

When beets imports all the files in a directory, it tries to remove the
directory if it\'s empty. A directory is considered empty if it only
contains files whose names match the glob patterns in
[clutter], which should be a list of strings. The default
list consists of \"Thumbs.DB\" and \".DS_Store\".

The importer only removes recursively searched subdirectories\-\--the
top-level directory you specify on the command line is never deleted.

### max_filename_length

Set the maximum number of characters in a filename, after which names
will be truncated. By default, beets tries to ask the filesystem for the
correct maximum.

### id3v23

By default, beets writes MP3 tags using the ID3v2.4 standard, the latest
version of ID3. Enable this option to instead use the older ID3v2.3
standard, which is preferred by certain older software such as Windows
Media Player.

### va_name

Sets the albumartist for various-artist compilations. Defaults to
`'Various Artists'` (the MusicBrainz standard). Affects other sources,
such as `/plugins/discogs`, too.

## UI Options

The options that allow for customization of the visual appearance of the
console interface.

These options are available in this section:

### color

Either `yes` or `no`; whether to use color in console output (currently
only in the `import` command). Turn this off if your terminal doesn\'t
support ANSI colors.

The [color] option was previously a top-level configuration.
This is still respected, but a deprecation message will be shown until
your top-level [color] configuration has been nested under
[ui].

### colors

The colors that are used throughout the user interface. These are only
used if the `color` option is set to `yes`. For example, you might have
a section in your configuration file that looks like this:

    ui:
        color: yes
        colors:
            text_success: green
            text_warning: yellow
            text_error: red
            text_highlight: red
            text_highlight_minor: lightgray
            action_default: turquoise
            action: blue

Available colors: black, darkred, darkgreen, brown (darkyellow),
darkblue, purple (darkmagenta), teal (darkcyan), lightgray, darkgray,
red, green, yellow, blue, fuchsia (magenta), turquoise (cyan), white

## Importer Options

The options that control the `import-cmd`
command are indented under the `import:` key. For example, you might
have a section in your configuration file that looks like this:

    import:
        write: yes
        copy: yes
        resume: no

These options are available in this section:

### write

Either `yes` or `no`, controlling whether metadata (e.g., ID3) tags are
written to files when using `beet import`. Defaults to `yes`. The `-w`
and `-W` command-line options override this setting.

### copy

Either `yes` or `no`, indicating whether to **copy** files into the
library directory when using `beet import`. Defaults to `yes`. Can be
overridden with the `-c` and `-C` command-line options.

The option is ignored if `move` is enabled (i.e., beets can move or copy
files but it doesn\'t make sense to do both).

### move

Either `yes` or `no`, indicating whether to **move** files into the
library directory when using `beet import`. Defaults to `no`.

The effect is similar to the `copy` option but you end up with only one
copy of the imported file. (\"Moving\" works even across filesystems; if
necessary, beets will copy and then delete when a simple rename is
impossible.) Moving files can be risky---it\'s a good idea to keep a
backup in case beets doesn\'t do what you expect with your files.

This option *overrides* `copy`, so enabling it will always move (and not
copy) files. The `-c` switch to the `beet import` command, however,
still takes precedence.

### link

Either `yes` or `no`, indicating whether to use symbolic links instead
of moving or copying files. (It conflicts with the `move`, `copy` and
`hardlink` options.) Defaults to `no`.

This option only works on platforms that support symbolic links: i.e.,
Unixes. It will fail on Windows.

It\'s likely that you\'ll also want to set `write` to `no` if you use
this option to preserve the metadata on the linked files.

### hardlink

Either `yes` or `no`, indicating whether to use hard links instead of
moving, copying, or symlinking files. (It conflicts with the `move`,
`copy`, and `link` options.) Defaults to `no`.

As with symbolic links (see `link`,
above), this will not work on Windows and you will want to set `write`
to `no`. Otherwise, metadata on the original file will be modified.

### reflink

Either `yes`, `no`, or `auto`, indicating whether to use copy-on-write
[file
clones](https://blogs.oracle.com/otn/save-disk-space-on-linux-by-cloning-files-on-btrfs-and-ocfs2)
(a.k.a. \"reflinks\") instead of copying or moving files. The `auto`
option uses reflinks when possible and falls back to plain copying when
necessary. Defaults to `no`.

This kind of clone is only available on certain filesystems: for
example, btrfs and APFS. For more details on filesystem support, see the
[pyreflink](https://reflink.readthedocs.io/en/latest/) documentation.
Note that you need to install `pyreflink`, either through
`python -m pip install beets[reflink]` or
`python -m pip install reflink`.

The option is ignored if `move` is enabled (i.e., beets can move or copy
files but it doesn\'t make sense to do both).

### resume

Either `yes`, `no`, or `ask`. Controls whether interrupted imports
should be resumed. \"Yes\" means that imports are always resumed when
possible; \"no\" means resuming is disabled entirely; \"ask\" (the
default) means that the user should be prompted when resuming is
possible. The `-p` and `-P` flags correspond to the \"yes\" and \"no\"
settings and override this option.

### incremental

Either `yes` or `no`, controlling whether imported directories are
recorded and whether these recorded directories are skipped. This
corresponds to the `-i` flag to `beet import`.

### incremental_skip_later

Either `yes` or `no`, controlling whether skipped directories are
recorded in the incremental list. When set to `yes`, skipped directories
won\'t be recorded, and beets will try to import them again later. When
set to `no`, skipped directories will be recorded, and skipped later.
Defaults to `no`.

### from_scratch

Either `yes` or `no` (default), controlling whether existing metadata is
discarded when a match is applied. This corresponds to the
`--from_scratch` flag to `beet import`.

### quiet

Either `yes` or `no` (default), controlling whether to ask for a manual
decision from the user when the importer is unsure how to proceed. This
corresponds to the `--quiet` flag to `beet import`.

### quiet_fallback

Either `skip` (default) or `asis`, specifying what should happen in
quiet mode (see the `-q` flag to `import`, above) when there is no
strong recommendation.

### none_rec_action

Either `ask` (default), `asis` or `skip`. Specifies what should happen
during an interactive import session when there is no recommendation.
Useful when you are only interested in processing medium and strong
recommendations interactively.

### timid

Either `yes` or `no`, controlling whether the importer runs in *timid*
mode, in which it asks for confirmation on every autotagging match, even
the ones that seem very close. Defaults to `no`. The `-t` command-line
flag controls the same setting.

### log

Specifies a filename where the importer\'s log should be kept. By
default, no log is written. This can be overridden with the `-l` flag to
`import`.

### default_action

One of `apply`, `skip`, `asis`, or `none`, indicating which option
should be the *default* when selecting an action for a given match. This
is the action that will be taken when you type return without an option
letter. The default is `apply`.

### languages

A list of locale names to search for preferred aliases. For example,
setting this to `en` uses the transliterated artist name \"Pyotr Ilyich
Tchaikovsky\" instead of the Cyrillic script for the composer\'s name
when tagging from MusicBrainz. You can use a space-separated list of
language abbreviations, like `en jp es`, to specify a preference order.
Defaults to an empty list, meaning that no language is preferred.

### detail

Whether the importer UI should show detailed information about each
match it finds. When enabled, this mode prints out the title of every
track, regardless of whether it matches the original metadata. (The
default behavior only shows changes.) Default: `no`.

### group_albums

By default, the beets importer groups tracks into albums based on the
directories they reside in. This option instead uses files\' metadata to
partition albums. Enable this option if you have directories that
contain tracks from many albums mixed together.

The `--group-albums` or `-g` option to the
`import-cmd` command is equivalent, and
the *G* interactive option invokes the same workflow.

Default: `no`.

### autotag

By default, the beets importer always attempts to autotag new music. If
most of your collection consists of obscure music, you may be interested
in disabling autotagging by setting this option to `no`. (You can
re-enable it with the `-a` flag to the `import-cmd`
command.)

Default: `yes`.

### duplicate_action

Either `skip`, `keep`, `remove`, `merge` or `ask`. Controls how
duplicates are treated in import task. \"skip\" means that new
item(album or track) will be skipped; \"keep\" means keep both old and
new items; \"remove\" means remove old item; \"merge\" means merge into
one album; \"ask\" means the user should be prompted for the action each
time. The default is `ask`.

### bell

Ring the terminal bell to get your attention when the importer needs
your input.

Default: `no`.

### set_fields

A dictionary indicating fields to set to values for newly imported
music. Here\'s an example:

    set_fields:
        genre: 'To Listen'
        collection: 'Unordered'

Other field/value pairs supplied via the `--set` option on the
command-line override any settings here for fields with the same name.

Fields are set on both the album and each individual track of the album.
Fields are persisted to the media files of each track.

Default: `{}` (empty).

## MusicBrainz Options

You can instruct beets to use [your own MusicBrainz
database](https://musicbrainz.org/doc/MusicBrainz_Server/Setup) instead
of the [main server](https://musicbrainz.org/). Use the `host`, `https`
and `ratelimit` options under a `musicbrainz:` header, like so:

    musicbrainz:
        host: localhost:5000
        https: no
        ratelimit: 100

The `host` key, of course, controls the Web server hostname (and port,
optionally) that will be contacted by beets (default: musicbrainz.org).
The `https` key makes the client use HTTPS instead of HTTP. This setting
applies only to custom servers. The official MusicBrainz server always
uses HTTPS. (Default: no.) The server must have search indices enabled
(see [Building search
indexes](https://musicbrainz.org/doc/Development/Search_server_setup)).

The `ratelimit` option, an integer, controls the number of Web service
requests per second (default: 1). **Do not change the rate limit
setting** if you\'re using the main MusicBrainz server\-\--on this
public server, you\'re
[limited](https://musicbrainz.org/doc/XML_Web_Service/Rate_Limiting) to
one request per second.

### enabled

This option allows you to disable using MusicBrainz as a metadata
source. This applies if you use plugins that fetch data from alternative
sources and should make the import process quicker.

Default: `yes`.

### searchlimit

The number of matches returned when sending search queries to the
MusicBrainz server.

Default: `5`.

### extra_tags

By default, beets will use only the artist, album, and track count to
query MusicBrainz. Additional tags to be queried can be supplied with
the `extra_tags` setting. For example:

    musicbrainz:
        extra_tags: [year, catalognum, country, media, label]

This setting should improve the autotagger results if the metadata with
the given tags match the metadata returned by MusicBrainz.

Note that the only tags supported by this setting are the ones listed in
the above example.

Default: `[]`

### genres

Use MusicBrainz genre tags to populate (and replace if it\'s already
set) the `genre` tag. This will make it a list of all the genres tagged
for the release and the release-group on MusicBrainz, separated by \";
\" and sorted by the total number of votes. Default: `no`

## Autotagger Matching Options

You can configure some aspects of the logic beets uses when
automatically matching MusicBrainz results under the `match:` section.
To control how *tolerant* the autotagger is of differences, use the
`strong_rec_thresh` option, which reflects the distance threshold below
which beets will make a \"strong recommendation\" that the metadata be
used. Strong recommendations are accepted automatically (except in
\"timid\" mode), so you can use this to make beets ask your opinion more
or less often.

The threshold is a *distance* value between 0.0 and 1.0, so you can
think of it as the opposite of a *similarity* value. For example, if you
want to automatically accept any matches above 90% similarity, use:

    match:
        strong_rec_thresh: 0.10

The default strong recommendation threshold is 0.04.

The `medium_rec_thresh` and `rec_gap_thresh` options work similarly.
When a match is below the *medium* recommendation threshold or the
distance between it and the next-best match is above the *gap*
threshold, the importer will suggest that match but not automatically
confirm it. Otherwise, you\'ll see a list of options to choose from.

### max_rec

As mentioned above, autotagger matches have *recommendations* that
control how the UI behaves for a certain quality of match. The
recommendation for a certain match is based on the overall distance
calculation. But you can also control the recommendation when a specific
distance penalty is applied by defining *maximum* recommendations for
each field:

To define maxima, use keys under `max_rec:` in the `match` section. The
defaults are \"medium\" for missing and unmatched tracks and \"strong\"
(i.e., no maximum) for everything else:

    match:
        max_rec:
            missing_tracks: medium
            unmatched_tracks: medium

If a recommendation is higher than the configured maximum and the
indicated penalty is applied, the recommendation is downgraded. The
setting for each field can be one of `none`, `low`, `medium` or
`strong`. When the maximum recommendation is `strong`, no
\"downgrading\" occurs. The available penalty names here are:

-   source
-   artist
-   album
-   media
-   mediums
-   year
-   country
-   label
-   catalognum
-   albumdisambig
-   album_id
-   tracks
-   missing_tracks
-   unmatched_tracks
-   track_title
-   track_artist
-   track_index
-   track_length
-   track_id

### preferred

In addition to comparing the tagged metadata with the match metadata for
similarity, you can also specify an ordered list of preferred countries
and media types.

A distance penalty will be applied if the country or media type from the
match metadata doesn\'t match. The specified values are preferred in
descending order (i.e., the first item will be most preferred). Each
item may be a regular expression, and will be matched case
insensitively. The number of media will be stripped when matching
preferred media (e.g. \"2x\" in \"2xCD\").

You can also tell the autotagger to prefer matches that have a release
year closest to the original year for an album.

Here\'s an example:

    match:
        preferred:
            countries: ['US', 'GB|UK']
            media: ['CD', 'Digital Media|File']
            original_year: yes

By default, none of these options are enabled.

### ignored

You can completely avoid matches that have certain penalties applied by
adding the penalty name to the `ignored` setting:

    match:
        ignored: missing_tracks unmatched_tracks

The available penalties are the same as those for the
`max_rec` setting.

For example, setting `ignored: missing_tracks` will skip any album
matches where your audio files are missing some of the tracks. The
importer will not attempt to display these matches. It does not ignore
the fact that the album is missing tracks, which would allow these
matches to apply more easily. To do that, you\'ll want to adjust the
penalty for missing tracks.

### required

You can avoid matches that lack certain required information. Add the
tags you want to enforce to the `required` setting:

    match:
        required: year label catalognum country

No tags are required by default.

### ignored_media

A list of media (i.e., formats) in metadata databases to ignore when
matching music. You can use this to ignore all media that usually
contain video instead of audio, for example:

    match:
        ignored_media: ['Data CD', 'DVD', 'DVD-Video', 'Blu-ray', 'HD-DVD',
                        'VCD', 'SVCD', 'UMD', 'VHS']

No formats are ignored by default.

### ignore_data_tracks

By default, audio files contained in data tracks within a release are
included in the album\'s tracklist. If you want them to be included, set
it `no`.

Default: `yes`.

### ignore_video_tracks

By default, video tracks within a release will be ignored. If you want
them to be included (for example if you would like to track the
audio-only versions of the video tracks), set it to `no`.

Default: `yes`.

## Path Format Configuration

You can also configure the directory hierarchy beets uses to store
music. These settings appear under the `paths:` key. Each string is a
template string that can refer to metadata fields like `$artist` or
`$title`. The filename extension is added automatically. At the moment,
you can specify three special paths: `default` for most releases, `comp`
for \"various artist\" releases with no dominant artist, and `singleton`
for non-album tracks. The defaults look like this:

    paths:
        default: $albumartist/$album%aunique{}/$track $title
        singleton: Non-Album/$artist/$title
        comp: Compilations/$album%aunique{}/$track $title

Note the use of `$albumartist` instead of `$artist`; this ensures that
albums will be well-organized. For more about these format strings, see
`pathformat`. The `aunique{}` function
ensures that identically-named albums are placed in different
directories; see `aunique` for details.

In addition to `default`, `comp`, and `singleton`, you can condition
path queries based on beets queries (see
`/reference/query`). This means that a
config file like this:

    paths:
        albumtype:soundtrack: Soundtracks/$album/$track $title

will place soundtrack albums in a separate directory. The queries are
tested in the order they appear in the configuration file, meaning that
if an item matches multiple queries, beets will use the path format for
the *first* matching query.

Note that the special `singleton` and `comp` path format conditions are,
in fact, just shorthand for the explicit queries `singleton:true` and
`comp:true`. In contrast, `default` is special and has no query
equivalent: the `default` format is only used if no queries match.

## Configuration Location

The beets configuration file is usually located in a standard location
that depends on your OS, but there are a couple of ways you can tell
beets where to look.

### Environment Variable

First, you can set the `BEETSDIR` environment variable to a directory
containing a `config.yaml` file. This replaces your configuration in the
default location. This also affects where auxiliary files, like the
library database, are stored by default (that\'s where relative paths
are resolved to). This environment variable is useful if you need to
manage multiple beets libraries with separate configurations.

### Command-Line Option

Alternatively, you can use the `--config` command-line option to
indicate a YAML file containing options that will then be merged with
your existing options (from `BEETSDIR` or the default locations). This
is useful if you want to keep your configuration mostly the same but
modify a few options as a batch. For example, you might have different
strategies for importing files, each with a different set of importer
options.

### Default Location

In the absence of a `BEETSDIR` variable, beets searches a few places for
your configuration, depending on the platform:

-   On Unix platforms, including OS X:`~/.config/beets` and then
    `$XDG_CONFIG_DIR/beets`, if the environment variable is set.
-   On OS X, we also search `~/Library/Application Support/beets` before
    the Unixy locations.
-   On Windows: `~\AppData\Roaming\beets`, and then `%APPDATA%\beets`,
    if the environment variable is set.

Beets uses the first directory in your platform\'s list that contains
`config.yaml`. If no config file exists, the last path in the list is
used.

## Example

Here\'s an example file:

    directory: /var/mp3
    import:
        copy: yes
        write: yes
        log: beetslog.txt
    art_filename: albumart
    plugins: bpd
    pluginpath: ~/beets/myplugins
    ui:
        color: yes

    paths:
        default: $genre/$albumartist/$album/$track $title
        singleton: Singletons/$artist - $title
        comp: $genre/$album/$track $title
        albumtype:soundtrack: Soundtracks/$album/$track $title

# Path Formats

The `paths:` section of the config file (see `config`)
lets you specify the directory and file naming scheme for
your music library. Templates substitute symbols like `$title` (any
field value prefixed by `$`) with the appropriate value from the
track\'s metadata. Beets adds the filename extension automatically.

For example, consider this path format string:
`$albumartist/$album/$track $title`

Here are some paths this format will generate:

-   `Yeah Yeah Yeahs/It's Blitz!/01 Zero.mp3`
-   `Spank Rock/YoYoYoYoYo/11 Competition.mp3`
-   `The Magnetic Fields/Realism/01 You Must Be Out of Your Mind.mp3`

Because `$` is used to delineate a field reference, you can use `$$` to
emit a dollars sign. As with [Python template
strings](https://docs.python.org/library/string.html#template-strings),
`${title}` is equivalent to `$title`; you can use this if you need to
separate a field name from the text that follows it.

## A Note About Artists

Note that in path formats, you almost certainly want to use
`$albumartist` and not `$artist`. The latter refers to the \"track
artist\" when it is present, which means that albums that have tracks
from different artists on them (like [Stop Making
Sense](https://musicbrainz.org/release/798dcaab-0f1a-4f02-a9cb-61d5b0ddfd36.html),
for example) will be placed into different folders! Continuing with the
Stop Making Sense example, you\'ll end up with most of the tracks in a
\"Talking Heads\" directory and one in a \"Tom Tom Club\" directory. You
probably don\'t want that! So use `$albumartist`.

As a convenience, however, beets allows `$albumartist` to fall back to
the value for `$artist` and vice-versa if one tag is present but the
other is not.

## Template Functions

Beets path formats also support *function calls*, which can be used to
transform text and perform logical manipulations. The syntax for
function calls is like this: `%func{arg,arg}`. For example, the `upper`
function makes its argument upper-case, so `%upper{beets rocks}` will be
replaced with `BEETS ROCKS`. You can, of course, nest function calls and
place variable references in function arguments, so `%upper{$artist}`
becomes the upper-case version of the track\'s artists.

These functions are built in to beets:

-   `%lower{text}`: Convert `text` to lowercase.
-   `%upper{text}`: Convert `text` to UPPERCASE.
-   `%title{text}`: Convert `text` to Title Case.
-   `%left{text,n}`: Return the first `n` characters of `text`.
-   `%right{text,n}`: Return the last `n` characters of `text`.
-   `%if{condition,text}` or `%if{condition,truetext,falsetext}`: If
    `condition` is nonempty (or nonzero, if it\'s a number), then
    returns the second argument. Otherwise, returns the third argument
    if specified (or nothing if `falsetext` is left off).
-   `%asciify{text}`: Convert non-ASCII characters to their ASCII
    equivalents. For example, \"café\" becomes \"cafe\". Uses the
    mapping provided by the [unidecode
    module](https://pypi.org/project/Unidecode). See the
    `asciify-paths` configuration option.
-   `%aunique{identifiers,disambiguators,brackets}`: Provides a unique
    string to disambiguate similar albums in the database. See
    `aunique`, below.
-   `%time{date_time,format}`: Return the date and time in any format
    accepted by
    [strftime](https://docs.python.org/3/library/time.html#time.strftime).
    For example, to get the year some music was added to your library,
    use `%time{$added,%Y}`.
-   `%first{text}`: Returns the first item, separated by `;` (a
    semicolon followed by a space). You can use
    `%first{text,count,skip}`, where `count` is the number of items
    (default 1) and `skip` is number to skip (default 0). You can also
    use `%first{text,count,skip,sep,join}` where `sep` is the separator,
    like `;` or `/` and join is the text to concatenate the items.
-   `%ifdef{field}`, `%ifdef{field,truetext}` or
    `%ifdef{field,truetext,falsetext}`: Checks if an flexible attribute
    `field` is defined. If it exists, then return `truetext` or `field`
    (default). Otherwise, returns `falsetext`. The `field` should be
    entered without `$`. Note that this doesn\'t work with built-in
    `itemfields`, as they are always
    defined.

Plugins can extend beets with more template functions (see
`templ_plugins`).

## Album Disambiguation

Occasionally, bands release two albums with the same name (c.f. Crystal
Castles, Weezer, and any situation where a single has the same name as
an album or EP). Beets ships with special support, in the form of the
`%aunique{}` template function, to avoid placing two identically-named
albums in the same directory on disk.

The `aunique` function detects situations where two albums have some
identical fields and emits text from additional fields to disambiguate
the albums. For example, if you have both Crystal Castles albums in your
library, `%aunique{}` will expand to \"\[2008\]\" for one album and
\"\[2010\]\" for the other. The function detects that you have two
albums with the same artist and title but that they have different
release years.

For full flexibility, the `%aunique` function takes three arguments. The
first two are whitespace-separated lists of album field names: a set of
*identifiers* and a set of *disambiguators*. The third argument is a
pair of characters used to surround the disambiguator.

Any group of albums with identical values for all the identifiers will
be considered \"duplicates\". Then, the function tries each
disambiguator field, looking for one that distinguishes each of the
duplicate albums from each other. The first such field is used as the
result for `%aunique`. If no field suffices, an arbitrary number is used
to distinguish the two albums.

The default identifiers are `albumartist album` and the default
disambiguators are
`albumtype year label catalognum albumdisambig releasegroupdisambig`. So
you can get reasonable disambiguation behavior if you just use
`%aunique{}` with no parameters in your path forms (as in the default
path formats), but you can customize the disambiguation if, for example,
you include the year by default in path formats.

The default characters used as brackets are `[]`. To change this,
provide a third argument to the `%aunique` function consisting of two
characters: the left and right brackets. Or, to turn off bracketing
entirely, leave argument blank.

One caveat: When you import an album that is named identically to one
already in your library, the *first* album---the one already in your
library--- will not consider itself a duplicate at import time. This
means that `%aunique{}` will expand to nothing for this album and no
disambiguation string will be used at its import time. Only the second
album will receive a disambiguation string. If you want to add the
disambiguation string to both albums, just run `beet move` (possibly
restricted by a query) to update the paths for the albums.

## Syntax Details

The characters `$`, `%`, `{`, `}`, and `,` are \"special\" in the path
template syntax. This means that, for example, if you want a `%`
character to appear in your paths, you\'ll need to be careful that you
don\'t accidentally write a function call. To escape any of these
characters (except `{`, and `,` outside a function argument), prefix it
with a `$`. For example, `$$` becomes `$`; `$%` becomes `%`, etc. The
only exceptions are:

-   `${`, which is ambiguous with the variable reference syntax (like
    `${title}`). To insert a `{` alone, it\'s always sufficient to just
    type `{`.
-   commas are used as argument separators in function calls. Inside of
    a function\'s argument, use `$,` to get a literal `,` character.
    Outside of any function argument, escaping is not necessary: `,` by
    itself will produce `,` in the output.

If a value or function is undefined, the syntax is simply left
unreplaced. For example, if you write `$foo` in a path template, this
will yield `$foo` in the resulting paths because \"foo\" is not a valid
field name. The same is true of syntax errors like unclosed `{}` pairs;
if you ever see template syntax constructs leaking into your paths,
check your template for errors.

If an error occurs in the Python code that implements a function, the
function call will be expanded to a string that describes the exception
so you can debug your template. For example, the second parameter to
`%left` must be an integer; if you write `%left{foo,bar}`, this will be
expanded to something like `<ValueError: invalid literal for int()>`.

## Available Values

Here\'s a list of the different values available to path formats. The
current list can be found definitively by running the command
`beet fields`. Note that plugins can add new (or replace existing)
template values (see `templ_plugins`).

Ordinary metadata:

-   title
-   artist
-   artist_sort: The \"sort name\" of the track artist (e.g., \"Beatles,
    The\" or \"White, Jack\").
-   artist_credit: The track-specific [artist
    credit](https://wiki.musicbrainz.org/Artist_Credit) name, which may
    be a variation of the artist\'s \"canonical\" name.
-   album
-   albumartist: The artist for the entire album, which may be different
    from the artists for the individual tracks.
-   albumartist_sort
-   albumartist_credit
-   genre
-   composer
-   grouping
-   year, month, day: The release date of the specific release.
-   original_year, original_month, original_day: The release date of the
    original version of the album.
-   track
-   tracktotal
-   disc
-   disctotal
-   lyrics
-   comments
-   bpm
-   comp: Compilation flag.
-   albumtype: The MusicBrainz album type; the MusicBrainz wiki has a
    [list of type
    names](https://musicbrainz.org/doc/Release_Group/Type).
-   label
-   asin
-   catalognum
-   script
-   language
-   country
-   albumstatus
-   media
-   albumdisambig
-   disctitle
-   encoder

Audio information:

-   length (in seconds)
-   bitrate (in kilobits per second, with units: e.g., \"192kbps\")
-   bitrate_mode (e.g., \"CBR\", \"VBR\" or \"ABR\", only available for
    the MP3 format)
-   encoder_info (e.g., \"LAME 3.97.0\", only available for some
    formats)
-   encoder_settings (e.g., \"-V2\", only available for the MP3 format)
-   format (e.g., \"MP3\" or \"FLAC\")
-   channels
-   bitdepth (only available for some formats)
-   samplerate (in kilohertz, with units: e.g., \"48kHz\")

MusicBrainz and fingerprint information:

-   mb_trackid
-   mb_releasetrackid
-   mb_albumid
-   mb_artistid
-   mb_albumartistid
-   mb_releasegroupid
-   acoustid_fingerprint
-   acoustid_id

Library metadata:

-   mtime: The modification time of the audio file.
-   added: The date and time that the music was added to your library.
-   path: The item\'s filename.

## Template functions and values provided by plugins

Beets plugins can provide additional fields and functions to templates.
See the `/plugins/index` page for a full
list of plugins. Some plugin-provided constructs include:

-   `$missing` by `/plugins/missing`: The
    number of missing tracks per album.
-   `%bucket{text}` by `/plugins/bucket`:
    Substitute a string by the range it belongs to.
-   `%the{text}` by `/plugins/the`: Moves
    English articles to ends of strings.

The `/plugins/inline` lets you define
template fields in your beets configuration file using Python snippets.
And for more advanced processing, you can go all-in and write a
dedicated plugin to register your own fields and functions (see
`writing-plugins`).

## See Also

`https://beets.readthedocs.org/`

`beet(1)`
