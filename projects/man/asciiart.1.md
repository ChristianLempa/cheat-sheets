---
title: ASCIIART
section: 1
header: User Manual
footer: asciiart 1.0.0
date: March 27, 2022
---
## NAME
asciiart - Display an ASCIImatics animated series of ascii art

## SYNOPSIS
**asciiart** [-h] [-d] [-a AUDIO] [-c CYCLE]

## DESCRIPTION
The *asciiart* command plays one of the ASCIImatics animations included in
Asciiville. Command line options can be used to tell *asciiart* to play
animations for a specified number of cycles and which audio file to use
as accompaniment.

## COMMAND LINE OPTIONS
**-h, --help**
: show this help message and exit

**-d, --debug**
: enable debug mode

**-a AUDIO, --audio AUDIO**
: audio file to play during effects

**-c CYCLE, --cycle CYCLE**
: number of times to cycle back through effects

## EXAMPLES
**asciiart**
: Without options asciiart will display an animated series of ascii art images. These will continue until the 'q' key is pressed.

**asciiart -c 10**
: Plays the Art Images ASCIImatics animation 10 times then exits 

**asciiart -a /usr/share/asciiville/music/Epic_Dramatic-Yuriy_Bespalov.wav -c 5**
: Plays the Art Images ASCIImatics animation 5 times accompanied by audio then exits 

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
ASCIIART is distributed under an Open Source license.
See the file LICENSE in the ASCIIART source distribution
for information on terms &amp; conditions for accessing and
otherwise using ASCIIART and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

