---
title: MPD-CONFIGURE
section: 1
header: User Manual
footer: mpd-configure 1.0.0
date: September 13, 2022
---
## NAME
mpd-configure - create a configuration file for the Music Player Daemon (MPD)

## SYNOPSIS
**mpd-configure** [-o PATH] [-l a|d|u] [-c REGEXP] [-a HWADDRESS] [-q] [--nobackup]

## DESCRIPTION

The `mpd-configure` bash script creates a valid configuration file for
[mpd], optimised for bit perfect playback of any digital audio file,
including those of high resolution.

With default settings the script uses the first available alsa audio
interface by using its hardware address (in the form of `hw:x,y`), and
has automagic procedures for things like the music directory and
directory where files are stored, the number of items in the music
direcory and the UPNP name. When multiple audio interfaces are found,
the user is presented with a choice.

## USAGE

The scripts lists all available alsa playback devices on the host. If
multiple are found, the user is prompted to enter the hardware address
of the device to be used. The `-n` (`--noprompts`) option skips the
prompt and uses the first interface found instead. The `-l`
(`--limit`), `-c` (`--customfilter`) and `-a` (`--address`) may
be used to filter the returned alsa devices.

```
-o PATH, --outputfile PATH    
    Saves the result in the file specified with `PATH'.
    When this is an existing file, the scripts prompts
    the user to overwrite it, and makes a backup of the
    original file unless the `--nobackup' option is used).
-l TYPEFILTER, --limit TYPEFILTER   
    Limit the list of available audio interfaces to
    TYPEFILTER. Can be one of `a' (or `analog'),
    `d' (or `digital'), `u' (or `usb'), the
    latter for USB Audio Class (UAC1 or UAC2) devices.
-c REGEXP, --customlimit REGEXP 
    Limit the list further to match `REGEXP'.
-a HWADDRESS, --address HWADDRESS   
    Limits the list further by the audio interface
    specified with HWADDRESS, eg. `hw:0,1'.
-q, --quiet
    Surpress listing each interface with its details,
    ie. only store the details of each card in the appropriate arrays.
-n, --noprompts
    Surpress prompting for the interface to use
    and/or to overwrite an existing conffile. Use the
    first available interface (matching the filters) instead.
--nobackup
    By default the scripts backs up an existing output file
    before overwriting. Setting this option prevents that and
    overwrites the file without making a backup.
-h, --help
    Show this help message and exit.
```

### Running the script

Run the script with default settings to display the contents of the
resulting mpd configuration file:

```bash
mpd-configure
```

### Storing the output of the script in a file

The output of the scripts can simply be redirected to a file (in this
example `mympd.conf`):

```bash
mpd-configure > mympd.conf
```

Although the same may be achieved by using the `-o` or `--output`
command line parameters or setting `CONF_MPD_CONFFILE` on the command
line. This has the benefit that the script detects if the target file
exists, in which case the user is prompted to overwrite it, while
making an automated *backup* of the original file:

```bash
mpd-configure -o "mympd.conf"
# or:
CONF_MPD_CONFFILE="mympd.conf" mpd-configure
```

### More advanced usage example

Additional setting are available using environment variables or using
the file `/usr/share/musicplayerplus/mpd/mpd-configure/mpd-configure.conf`
and configuration snippet files in the
`/usr/share/musicplayerplus/mpd/mpd-configure/confs-available/` directory. 

For example to specify `CONF_MPD_MUSICDIR` which sets the
`music_directory` and saving the resulting mpd configuration file in
`mympd.conf`, use:

```bash
CONF_MPD_MUSICDIR="/srv/media/music" mpd-configure -o "mympd.conf"
```

By default `mpd-configure` prompts the user to overwrite the specified
file if it exists, and makes a backup of it.

### Fully automated usage example

A fully automated example which does not prompt the user (`-n`), uses the
first available USB Audio Class interface (`-l u`) and sets some paths, while
creating a backup of the original `/etc/mpd.conf` in case it exists:

```bash
CONF_MPD_MUSICDIR="/srv/media/music" CONF_MPD_HOMEDIR="/var/lib/mpd" \
mpd-configure -l u -n -o "/etc/mpd.conf"
```

To see all available command line options run the script with `-h` or `--help`:
```bash
mpd-configure -h
```

`mpd-configure` relies on the accompanying bash script `alsa-capabilities`
for getting information about the available audio output interfaces from alsa. 


### Detailed usage instructions

After creating a mpd configuration file, `mpd` can be told to use this
configuration file with:

```
    mpd ./mpd.conf
```

To use the generated configuration file system wide, it can be copied
to the system wide mpd configuration file when you want to run `mpd`
as a system daemon:

```
    sudo mpd-configure -o "/etc/mpd.conf"
    sudo systemctl restart mpd
```

### More complex usage

For debugging or testing purposes one may set the `INCLUDE_COMMENTS`
and/or `DEBUG` parameters through the `mpd-configure.conf` file or on
the command line, eg:

```
    DEBUG="True" INCLUDE_COMMENTS="True" mpd-configure
```    

In dynamic environments in which hardware may be altered each boot,
connected to whatever USB DAC, the script could be put in a logon script
or systemd service file.

### Usage as a systemd service

The script is fast and stable enough to function as a systemd
service. By setting `Before=mpd.service` and `Wants=mpd.service` in
the service file systemd makes sure mpd-configure is run before mpd is
started, and tries to start mpd.


### Usage from within another bash or sh script

The bash script
`/usr/share/musicplayerplus/mpd/mpd-configure/examples/bash-example.sh`
demonstrates the way alsa-capabilities can be used from another bash script.

This demo script returns the monitoring file of the file specified as
an argument:

```
bash examples/bash-example.sh hw:1,0
```

Result:
```
the audio card with alsa hardware address hw:1,0 can be monitored with:
/proc/asound/card1/stream0
```


### Usage from within python

Assuming your in the `/usr/share/musicplayerplus/mpd/mpd-configure` directory,
run:
```
    python examples/get-interfaces.py
```

The python script `./examples/get-interfaces.py` uses a helper bash script
(`./examples/get-interfaces-for-python.sh`), which in turn sources
`alsa-capabilities`.

## PREFERENCES

Preferences can be set in the file
`/usr/share/musicplayerplus/mpd/mpd-configure/mpd-configure.conf`.
By default all preferences are commented out.

The script uses configuration file snippets in the
`./confs-available/` directory. By symlinking
them to the `./confs-enabled/` directory, they will
be included by `mpd-configure` in the resulting mpd configuration
file. Any bash variable in those configuration snippets, will be
expanded to their calculated values by the script.

### General environment variables

`DEBUG`
Output values of variables and program flow to std_err for easier
debugging. Possible values:
- commented out: disabled (Default).
- `1` (or non-empty): enabled.


`INCLUDE_COMMENTS`
Include commented and empty lines from configuration snippet files in
the generated mpd configuration file:
- commentend out: disabled (Default).
- `1` (or non-empty): enabled


`CONF_MPD_CONFFILE`
Path to where the generated mpd configuration file will be
written. Possible values:
- commented out: don't write to a file (Default). One may redirect the
  output of the script using:

  bash mpd-configure > /path/to/mpd.conf

- `/path/to/mpd.conf`: use the path specified.


### Alsa and sound

`LIMIT_INTERFACE_TYPE`
A keyword which limits the type of alsa interfaces to be returned: 

Possible values:
- `usb`, `digital` or `analog`
- Comment it out (or leave it empty) to prevent filtering.

Default value:
- commented out (or empty ""): do not limit the interfaces that will be found.


`LIMIT_INTERFACE_FILTER`
The available output devices (after filtering with
`LIMIT_INTERFACE_TYPE` when applicable) may be further limited using a
regular expression (which thus is case sensentive) which should match
the output of:

    LANG=C aplay -l | grep ^card

If for example the output is like this:

    card 0: MID [HDA Intel MID], device 0: HDMI 0 [HDMI 0]
    card 1: receiv [Pink Faun USB 32/384 USB receiv], device 0: USB Audio [USB Audio]

... you could use one of the following values to match the *second* line
(which in this example matches the alsa `hw:1,1` interface, eg. the
second interface of the second sound card):

    "USB Audio"
    "[uU][sS][bB] \w+ "

but not

    "USB audio"


Possible values:
- empty or commented out: no filtering is applied
- `Some regular expression`: use the (first) interface which matches the regexp.

Default value:
- commented out (or empty ""): use the first available interface. 

Handling of pulseaudio
`OPT_DISABLE_PULSEAUDIO`
Disable pulseaudio by modifyin the current users' `~/.pulseaudio/client.conf`

Possible values:
- non-empty (`1` or "True") disables pulseaudio.
- Comment it out (or leave it empty) to prevent disabling of pulseaudio.


Default value:
- commented out (or empty ""): do not disable it.

`OPT_STOP_PULSEAUDIO`
Temporary disable and stop pulseaudio during detection of alsa
interfaces. After the script pulseaudio's client configuration and run
state will restored.

Possible values:
- non-empty (`1` or "True") temporary disables and stops pulseaudio.
- Comment it out (or leave it empty) to prevent temporary disabling
  and stopping of pulseaudio.

Default value:
- commented out (or empty ""): do not disable it.

See the configuration snippet files and accompanying `README` in
`./confs-available` for additional parameters and and explanation for
their functions.

## AUTHORS
Written by Ronald van Engelen ronalde@lacocina.nl

Modified and adapted by Ronald Record github@ronrecord.com

## LICENSING
MPD-CONFIGURE is distributed under an Open Source license.
See the file LICENSE in the MPD-CONFIGURE source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPD-CONFIGURE and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpplus**(1), **alsa-capabilities**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus
