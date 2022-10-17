---
title: MPPCAVA
section: 1
header: User Manual
footer: mppcava 0.8.2
date: July 03, 2022
---
## NAME
mppcava - Console-based Audio Spectrum Visualizer for ALSA

## SYNOPSIS
**mppcava** [-v] [-p config]

Exit with `ctrl+c` or `q`.

## DESCRIPTION
The *mppcava* command is a bar spectrum audio visualizer for the Linux
terminal using ALSA, pulseaudio or fifo buffer for input.

This program is not intended for scientific use. It's written to look
responsive and aesthetic when used to visualize music. 

Read more about `mppcava` at
https://github.com/doctorfree/MusicPlayerPlus/tree/master/mppcava#readme

## CONTROLS

NOTE: only works in ncurses output mode.

| Key | Description |
| --- | ----------- |
| <kbd>up</kbd> / <kbd>down</kbd>| increase/decrease sensitivity |
| <kbd>left</kbd> / <kbd>right</kbd>| increase/decrease bar width |
| <kbd>f</kbd> / <kbd>b</kbd>| change foreground/background color |
| <kbd>r</kbd> | Reload configuration |
| <kbd>c</kbd> | Reload colors only |
| <kbd>q</kbd> or <kbd>CTRL-C</kbd>| Quit C.A.V.A. |

If *mppcava* quits unexpectedly or is force killed,
echo must be turned on manually with `stty -echo`.

## CONFIGURATION

All options are done in the config file, no more command-line arguments!

By default a configuration file is created upon first launch in
`$XDG_CONFIG_HOME/mppcava/config` or `$HOME/.config/mppcava/config`,
but mppcava can also be made to use a different file with the `-p` option.

Sending mppcava a SIGUSR1 signal, will force mppcava to reload its configuration
file. Thus, it behaves as if the user pressed <kbd>r</kbd> in the terminal.
One might send a SIGUSR1 signal using `pkill` or `killall`.
For example:
```
$ pkill -USR1 mppcava
```

Similarly, sending mppcava a SIGUSR2 signal will only reload the colors from
the configuration file, which is the same as pressing <kbd>c</kbd> in the
terminal. This is slightly faster than reloading the entire config as the
audio processing does not need to reinitialize.  
```
$ pkill -USR2 mppcava
```

## AUTHORS
Written by Karl Stavestrand karl@stavestrand.no
Modified by by Ronald Record github@ronrecord.com

## LICENSING
MPPCAVA is distributed under an Open Source license.
See the file LICENSE in the MPPCAVA source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPCAVA and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpplus**(1), **mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

