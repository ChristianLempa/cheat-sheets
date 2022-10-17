---
title: BTOP
section: 1
header: User Manual
footer: btop 1.2.9
date: April 27, 2022
---
## NAME
btop - Resource monitor that shows usage and stats for processor, memory, disks, network and processes.

## SYNOPSIS
**btop** [-h] [-v] [-/+t] [-p <id>] [--utf-force] [--debug]

## DESCRIPTION
The *btop* command is a C++ version and continuation of [bashtop](https://github.com/aristocratos/bashtop) and [bpytop](https://github.com/aristocratos/bpytop).

## COMMAND LINE OPTIONS

**-h, --help**
: show this help message and exit

**-v, --version**
: show version info and exit

**-lc, --low-color**
: disable truecolor, converts 24-bit colors to 256-color

**-t, --tty_on**
: force (ON) tty mode, max 16 colors and tty friendly graph symbols

**+t, --tty_off**
: force (OFF) tty mode

**-p, --preset <id>**
: start with preset, integer value between 0-9

**--utf-force**
: force start even if no UTF-8 locale was detected

**--debug**
: start in DEBUG mode: shows microsecond timer for information collect and screen draw functions and sets loglevel to DEBUG

## FEATURES

* Easy to use, with a game inspired menu system.
* Full mouse support, all buttons with a highlighted key is clickable and mouse scroll works in process list and menu boxes.
* Fast and responsive UI with UP, DOWN keys process selection.
* Function for showing detailed stats for selected process.
* Ability to filter processes.
* Easy switching between sorting options.
* Tree view of processes.
* Send any signal to selected process.
* UI menu for changing all config file options.
* Auto scaling graph for network usage.
* Shows IO activity and speeds for disks
* Battery meter
* Selectable symbols for the graphs
* Custom presets

## KEYBOARD / MOUSE CONTROLS

- **"Mouse 1"**
: Clicks buttons and selects in process list.

- **"Mouse scroll"**
: Scrolls any scrollable list/text under cursor.

- **"Esc, m"**
: Toggles main menu.

- **"p"**
: Cycle view presets forwards.

- **"shift + p"**
: Cycle view presets backwards.

- **"1"**
: Toggle CPU box.

- **"2"**
: Toggle MEM box.

- **"3"**
: Toggle NET box.

- **"4"**
: Toggle PROC box.

- **"d"**
: Toggle disks view in MEM box.

- **"F2, o"**
: Shows options.

- **"F1, h"**
: Shows this window.

- **"ctrl + z"**
: Sleep program and put in background.

- **"q, ctrl + c"**
: Quits program.

- **"-"**
: Add/Subtract 100ms to/from update timer.

- **"Up, Down"**
: Select in process list.

- **"Enter"**
: Show detailed information for selected process.

- **"Spacebar"**
: Expand/collapse the selected process in tree view.

- **"Pg Up, Pg Down"**
: Jump 1 page in process list.

- **"Home, End"**
: Jump to first or last page in process list.

- **"Left, Right"**
: Select previous/next sorting column.

- **"b, n"**
: Select previous/next network device.

- **"i"**
: Toggle disks io mode with big graphs.

- **"z"**
: Toggle totals reset for current network device

- **"a"**
: Toggle auto scaling for the network graphs.

- **"y"**
: Toggle synced scaling mode for network graphs.

- **"f, /"**
: To enter a process filter.

- **"delete"**
: Clear any entered filter.

- **"c"**
: Toggle per-core cpu usage of processes.

- **"r"**
: Reverse sorting order in processes box.

- **"e"**
: Toggle processes tree view.

- **"Selected +, -"**
: Expand/collapse the selected process in tree view.

- **"Selected t"**
: Terminate selected process with SIGTERM - 15.

- **"Selected k"**
: Kill selected process with SIGKILL - 9.

- **"Selected s"**
: Select or enter signal to send to process.

## THEMES

Btop++ uses the same theme files as bpytop and bashtop (some color values missing in bashtop themes) .

See [themes](https://github.com/doctorfree/Asciiville/tree/main/btop/themes) folder for available themes.

The default themes are in `/usr/share/btop/themes/`. User created themes should be placed in
`$XDG_CONFIG_HOME/btop/themes` or `$HOME/.config/btop/themes`.

## PREREQUISITES

For best experience, a terminal with support for:

* 24-bit truecolor ([See list of terminals with truecolor support](https://gist.github.com/XVilka/8346728))
* 256-color terminals are supported through 24-bit to 256-color conversion when setting "truecolor" to False in the options or with "-lc/--low-color" arguments.
* 16 color TTY mode will be activated if a real tty device is detected. Can be forced with "-t/--tty_on" arguments.
* Wide characters (Are sometimes problematic in web-based terminals)

Also needs a UTF8 locale and a font that covers:

* Unicode Block “Braille Patterns” U+2800 - U+28FF (Not needed in TTY mode or with graphs set to type: block or tty.)
* Unicode Block “Geometric Shapes” U+25A0 - U+25FF
* Unicode Block "Box Drawing" and "Block Elements" U+2500 - U+259F

## AUTHORS
Btop written by Jakob P. Liljenberg (jakob@qvantnet.com)

Btop man page and front-ends written by Ronald Record (github@ronrecord.com)

## LICENSING
BTOP is distributed under an Open Source license.
See the file LICENSE in the BTOP source distribution
for information on terms &amp; conditions for accessing and
otherwise using BTOP and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

