---
title: SHOW_MOON
section: 1
header: User Manual
footer: show_moon 1.0.0
date: May 01, 2022
---
## NAME
show_moon - Display the phase of the Moon

## SYNOPSIS
**show_moon** [-d date] [-h] [-L location] [-l lang] [-u]

## DESCRIPTION
The *show_moon* command displays the phase of the Moon in ANSI characters.
Command line options can be used to specify the date, location, and language.

## COMMAND LINE OPTIONS
**-h**
: indicates show online help message and exit

**-d 'date'**
: specifies the date to use for phase of Moon, specify the 'date' in format 'YYYY-MM-DD'

**-L 'location'**
: specifies the location key to use, specify a location as described in the help document

**-l 'lang'**
: specifies the language code

	Supported languages:
		am ar af be bn ca da de el et fr fa hi hu ia id it lt mg
        nb nl oc pl pt-br ro ru ta tr th uk vi zh-cn zh-tw

**-s**
: indicates use v2 server

**-u**
: indicates show this usage message and exit

## EXAMPLES
**show_moon**
: Without options show_moon will display the current phase of the Moon at your current location as given by your IP address

**show_moon -L Paris -l fr**
: Display the current phase of the Moon in Paris, France. Use French language text description.

**show_moon -d 2022-10-31**
: Display the phase of the Moon on October 31, 2022 at your current location as given by your IP address

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
SHOW_MOON is distributed under an Open Source license.
See the file LICENSE in the SHOW_MOON source distribution
for information on terms &amp; conditions for accessing and
otherwise using SHOW_MOON and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**show_pokemon**(1), **show_weather**(1), **asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

