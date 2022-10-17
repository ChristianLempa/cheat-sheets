---
title: SHOW_WEATHER
section: 1
header: User Manual
footer: show_weather 1.0.0
date: May 01, 2022
---
## NAME
show_weather - Display a weather report

## SYNOPSIS
**show_weather** [-f format] [-h] [-L location] [-l lang] [-u]

## DESCRIPTION
The *show_weather* command displays a weather report in ANSI characters.
Command line options can be used to specify the location, and language.

## COMMAND LINE OPTIONS

**-f 'format'**
: specifies a format string (default: AFQn1)

**-h**
: indicates show online help message and exit

**-L 'location'**
: specifies the location key to use

		Use any of the location types described in the help document
		Quote a location key that includes spaces

**-l 'lang'**
: specifies the language code

	Supported languages:
		am ar af be bn ca da de el et fr fa hi hu ia id it lt
		mg nb nl oc pl pt-br ro ru ta tr th uk vi zh-cn zh-tw

**-u**
: indicates show this usage message and exit

## EXAMPLES
**show_weather**
: Without options show_weather will display the current weather at your current location as given by your IP address

**show_weather -L Paris -l fr**
: Display the current weather in Paris, France. Use French language text description.

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
SHOW_WEATHER is distributed under an Open Source license.
See the file LICENSE in the SHOW_WEATHER source distribution
for information on terms &amp; conditions for accessing and
otherwise using SHOW_WEATHER and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**show_moon**(1), **show_pokemon**(1), **asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

