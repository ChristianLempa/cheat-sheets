---
title: ASCIIMPPLUS
section: 1
header: User Manual
footer: asciimpplus 1.0.0
date: March 27, 2022
---
## NAME
asciimpplus - Display an ASCIImatics animation featuring ascii art for the MusicPlayerPlus project

## SYNOPSIS
**asciimpplus** [-h] [-d] [-a AUDIO] [-c CYCLE] [-f font]

## DESCRIPTION
The *asciimpplus* command plays one of the ASCIImatics animations included in
Asciiville. Command line options can be used to tell *asciimpplus* to play
animations for a specified number of cycles, which audio file to use as
accompaniment, and specify the font used in the Cycle effect.

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
: Font for FigletText in Cycle effect, default 'small'

## EXAMPLES
**asciimpplus**
: Without options asciimpplus will display an ASCIImatics animation featuring MusicPlayerPlus. These will continue until the 'q' key is pressed.

**asciimpplus -c 10**
: Plays the MusicPlayerPlus ASCIImatics animation 10 times then exits 

**asciimpplus -a /usr/share/asciiville/music/Epic_Dramatic-Yuriy_Bespalov.wav -c 5**
: Plays the MusicPlayerPlus ASCIImatics animation 5 times accompanied by audio then exits 

**asciimpplus -f big**
: Plays the ASCIImatics animation using the 'big' FigletText font for the Cycle effect

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
ASCIIMPPLUS is distributed under an Open Source license.
See the file LICENSE in the ASCIIMPPLUS source distribution
for information on terms &amp; conditions for accessing and
otherwise using ASCIIMPPLUS and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciijulia**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

