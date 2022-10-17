---
title: ASCINIT
section: 1
header: User Manual
footer: ascinit 1.0.1
date: May 04, 2022
---
## NAME
ascinit - Asciiville initialization script

## SYNOPSIS
**ascinit** [-a] [-c] [-d] [-m] [-M] [-n] [-N] [-q] [-t] [-u]

## DESCRIPTION
The *ascinit* command should be run as a normal user with `sudo` privilege
after installing Asciiville. It performs several configuration initializations
for the user. These include:

* The Kitty terminal emulator is installed and configured
* Mutt and/or NeoMutt startup files are customized
* Tmux configuration is created
* default Ranger and Rifle configuration files are created
* Asciimatics and Rainbowstream installation is performed
* Optionally authorizing the Rainbow Stream app with Twitter
* Optionally additional terminal emulators can be installed and configured
* Asciiville profiles in Gnome and Tilix terminals are created, if installed

Although command line options are provided to control the action(s) of the
`ascinit` command (see below), the typical invocation will simply be `ascinit`
with no options. This default invocation performs a NeoMutt configuration,
does not configure Mutt, configures Tmux and Ranger and Rifle, installs
Asciimatics and Rainbowstream if not already installed, does not authorize
Rainbow Stream with Twitter, installs the Kitty terminal emulator, and creates
an Asciiville profile in gnome-terminal and tilix if installed.

If initialization is being performed on a headless system or a system
without graphical capabilities then execute the command `ascinit -c`
rather than `ascinit`. When invoked with the `-c` option the `ascinit`
command will not install the terminal emulators or create the terminal profiles.

## COMMAND LINE OPTIONS

**-a**
: indicates do not ask to play an animation when done

**-c**
: indicates console-only mode, no terminal emulators are installed or configured and several mailcap configurations specifically tailored for console use are installed

**-d**
: indicates debug mode

**-m**
: indicates setup user Mutt configuration

**-M**
: indicates setup both Mutt and NeoMutt configurations

**-n**
: indicates setup user NeoMutt configuration

**-N**
: indicates prompt for installation of additional terminal emulators

**-q**
: indicates quiet mode

**-t**
: indicates authorize the Rainbow Stream app at Twitter

**-u**
: indicates display this usage message and exit

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
ASCINIT is distributed under an Open Source license.
See the file LICENSE in the ASCINIT source distribution
for information on terms &amp; conditions for accessing and
otherwise using ASCINIT and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciiart**(1), **asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

