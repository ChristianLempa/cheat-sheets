---
title: MPCPLUS-TMUX
section: 1
header: User Manual
footer: mpcplus-tmux 1.0.0
date: March 26, 2022
---
## NAME
mpcplus-tmux - runs mpcplus, a visualizer, and displays album art in a tmux session

## SYNOPSIS
**mpcplus-tmux** [-a] [-A] [-c client] [-g] [-p script] [-r] [-u]

**NOTE:** `mpcplus-tmux` is typically run automatically by `mpplus` when `tmux` is used

## DESCRIPTION
The *mpcplus-tmux* command opens several panes in a terminal window,
executing the mpcplus MPD client in one pane, a visualizer in another pane,
and displaying album cover art in another pane. The album cover art
automatically updates when another album is selected in the MPD client pane.
The visualizer pane displays, by default, the `mppcava` spectrum visualizer.
Alternately, the visualizer pane can display a Python ASCIImatics visualization.

## COMMAND LINE OPTIONS

Defaults: cover art enabled, ascii art disabled, recording disabled

**-a**
: Indicates display album cover art using original method

**-A**
: Indicates disable display of album cover art

**-c client**
: Specifies an MPD client to run in the client pane (album cover art is enabled for `mpcplus` and `ncmpcpp` MPD clients only)

**-g**
: Indicates do not use gradient colors for spectrum visualizer

**-p script**
: Specifies a python script to run in the visualizer pane. Available scripts are "julia", "plasma", and "rocks".

**-r**
: Indicates record tmux session with asciinema (album cover art not recorded)

**-u**
: Displays this usage message and exits

**Defaults:**
: cover art enabled, python art disabled, recording disabled

## EXAMPLES
**mpcplus-tmux**
: Without options, *mpcplus-tmux* displays the mpcplus MPD client, mppcava spectrum visualizer, and album cover art in a tmux session. 

**mpcplus-tmux -A**
: With the -A option, *mpcplus-tmux* displays the mpcplus MPD client and mppcava spectrum visualizer. No album cover art is displayed.

**mpcplus-tmux -a**
: With the -a option, *mpcplus-tmux* displays the mpcplus MPD client, mppcava spectrum visualizer, and album cover art using the original art display method

**mpcplus-tmux -p plasma**
: With the -p plasma option, *mpcplus-tmux* displays the mpcplus MPD client and plasma ASCIImatics display in a tmux session. 

**mpcplus-tmux -r**
: With the -r option, *mpcplus-tmux* displays the mpcplus MPD client and mppcava spectrum visualizer in a tmux session and records the session using asciinema. Recordings are stored in the user's `$HOME/Videos/` folder.

## TMUX Cheat Sheet References

* https://tmuxcheatsheet.com/
* https://gist.github.com/MohamedAlaa/2961058

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPCPLUS-TMUX is distributed under an Open Source license.
See the file LICENSE in the MPCPLUS-TMUX source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPCPLUS-TMUX and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpcplus**(1), **mpcpluskeys**(1), **mpplus**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

