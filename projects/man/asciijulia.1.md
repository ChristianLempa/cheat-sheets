---
title: ASCIIJULIA
section: 1
header: User Manual
footer: asciijulia 1.0.0
date: March 27, 2022
---
## NAME
asciijulia - Display an ASCIImatics animated zoom on a Julia Set

## SYNOPSIS
**asciijulia** [-h] [-d] [-i] [-a AUDIO] [-c CYCLE] [-x XVALUE] [-y YVALUE]

## DESCRIPTION
The *asciijulia* command plays one of the ASCIImatics animations included in
Asciiville. Command line options can be used to tell *asciijulia* to play
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
**asciijulia**
: Without options asciijulia will display an animated zoom on a Julia Set. These will continue until the 'q' key is pressed.

**asciijulia -c 10**
: Plays the Julia Set ASCIImatics animation 10 times then exits 

**asciijulia -a /usr/share/asciiville/music/Epic_Dramatic-Yuriy_Bespalov.wav -c 5**
: Plays the Julia Set ASCIImatics animation 5 times accompanied by audio then exits 

**asciijulia -x 0.687 -y 0.312**
: Display an animated zoom on the Julia Set with starting complex coordinates [0.687, 0.312]

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
ASCIIJULIA is distributed under an Open Source license.
See the file LICENSE in the ASCIIJULIA source distribution
for information on terms &amp; conditions for accessing and
otherwise using ASCIIJULIA and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

