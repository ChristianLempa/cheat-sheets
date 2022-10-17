---
title: MPPPLASMA
section: 1
header: User Manual
footer: mppplasma 1.0.0
date: March 27, 2022
---
## NAME
mppplasma - Display an ASCIImatics animation featuring the Plasma effect

## SYNOPSIS
**mppplasma** [-h] [-d] [-a AUDIO] [-c CYCLE] [-f FONT] [-t]

## DESCRIPTION
The *mppplasma* command plays one of the ASCIImatics animations included in
MusicPlayerPlus. Command line options can be used to tell *mppplasma* to play
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
**mppplasma**
: Without options mppplasma will display an ASCIImatics animation featuring the Plasma effect. These will continue until the 'q' key is pressed.

**mppplasma -c 10**
: Plays the Plasma ASCIImatics animation 10 times then exits 

**mppplasma -a /usr/share/musicplayerplus/music/Epic_Dramatic-Yuriy_Bespalov.wav -c 5**
: Plays the Plasma ASCIImatics animation 5 times accompanied by audio then exits 

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPPPLASMA is distributed under an Open Source license.
See the file LICENSE in the MPPPLASMA source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPPLASMA and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

