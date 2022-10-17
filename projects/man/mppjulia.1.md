---
title: MPPJULIA
section: 1
header: User Manual
footer: mppjulia 1.0.0
date: March 27, 2022
---
## NAME
mppjulia - Display an ASCIImatics animated zoom on a Julia Set

## SYNOPSIS
**mppjulia** [-h] [-d] [-i] [-a AUDIO] [-c CYCLE] [-x XVALUE] [-y YVALUE]

## DESCRIPTION
The *mppjulia* command plays one of the ASCIImatics animations included in
MusicPlayerPlus. Command line options can be used to tell *mppjulia* to play
animations for a specified number of cycles, what complex number to use as the
starting point for calculations, and which audio file to use as accompaniment.

## COMMAND LINE OPTIONS
**-h, --help**
: show this help message and exit

**-d, --debug**
: enable debug mode

**-i, --info**
: show an information screen prior to displaying the Julia Set zoom

**-a AUDIO, --audio AUDIO**
: audio file to play during effects

**-c CYCLE, --cycle CYCLE**
: number of times to cycle back through effects

**-x XVALUE, --xvalue XVALUE**
: starting x value of 'c' for the Julia set

**-y YVALUE, --yvalue YVALUE**
: starting y value of 'c' for the Julia set

## EXAMPLES
**mppjulia**
: Without options mppjulia will display an animated zoom on a Julia Set. These will continue until the 'q' key is pressed.

**mppjulia -c 10**
: Plays the Julia Set ASCIImatics animation 10 times then exits 

**mppjulia -a /usr/share/musicplayerplus/music/Epic_Dramatic-Yuriy_Bespalov.wav -c 5**
: Plays the Julia Set ASCIImatics animation 5 times accompanied by audio then exits 

**mppjulia -x 0.687 -y 0.312**
: Display an animated zoom on the Julia Set with starting complex coordinates [0.687, 0.312]

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPPJULIA is distributed under an Open Source license.
See the file LICENSE in the MPPJULIA source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPJULIA and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

