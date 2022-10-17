---
title: MPPROCKS
section: 1
header: User Manual
footer: mpprocks 1.0.0
date: March 27, 2022
---
## NAME
mpprocks - Display an ASCIImatics animation featuring ascii art for the MusicPlayerPlus project

## SYNOPSIS
**mpprocks** [-h] [-d] [-a AUDIO] [-c CYCLE] [-f font]

## DESCRIPTION
The *mpprocks* command plays one of the ASCIImatics animations included in
MusicPlayerPlus. Command line options can be used to tell *mpprocks* to play
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
**mpprocks**
: Without options mpprocks will display an ASCIImatics animation featuring MusicPlayerPlus. These will continue until the 'q' key is pressed.

**mpprocks -c 10**
: Plays the MusicPlayerPlus ASCIImatics animation 10 times then exits 

**mpprocks -a /usr/share/musicplayerplus/music/Epic_Dramatic-Yuriy_Bespalov.wav -c 5**
: Plays the MusicPlayerPlus ASCIImatics animation 5 times accompanied by audio then exits 

**mpprocks -f big**
: Plays the ASCIImatics animation using the 'big' FigletText font for the Cycle effect

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPPROCKS is distributed under an Open Source license.
See the file LICENSE in the MPPROCKS source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPROCKS and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

