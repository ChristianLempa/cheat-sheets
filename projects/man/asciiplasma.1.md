---
title: ASCIIPLASMA
section: 1
header: User Manual
footer: asciiplasma 1.0.0
date: March 27, 2022
---
## NAME
asciiplasma - Display an ASCIImatics animation featuring the Plasma effect

## SYNOPSIS
**asciiplasma** [-h] [-d] [-a AUDIO] [-c CYCLE] [-f FONT] [-t]

## DESCRIPTION
The *asciiplasma* command plays one of the ASCIImatics animations included in
Asciiville. Command line options can be used to tell *asciiplasma* to play
animations for a specified number of cycles, which FigletText font to use,
which audio file to use as accompaniment, and which comments to use.

## COMMAND LINE OPTIONS
**-h, --help**
: show this help message and exit

**-a AUDIO, --audio AUDIO**
: audio file to play during effects

**-c CYCLE, --cycle CYCLE**
: number of times to cycle back through effects

**-d, --debug**
: enable debug mode

**-f FONT, --font FONT**
: Font for FigletText, default 'banner3'

**-t, --text**
: Use alternate set of comments

## EXAMPLES
**asciiplasma**
: Without options asciiplasma will display an ASCIImatics animation featuring the Plasma effect. These will continue until the 'q' key is pressed.

**asciiplasma -c 10**
: Plays the Plasma ASCIImatics animation 10 times then exits 

**asciiplasma -a /usr/share/asciiville/music/Epic_Dramatic-Yuriy_Bespalov.wav -c 5**
: Plays the Plasma ASCIImatics animation 5 times accompanied by audio then exits 

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
ASCIIPLASMA is distributed under an Open Source license.
See the file LICENSE in the ASCIIPLASMA source distribution
for information on terms &amp; conditions for accessing and
otherwise using ASCIIPLASMA and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciijulia**(1), **asciimpplus**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

