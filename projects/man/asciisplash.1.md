---
title: ASCIISPLASH
section: 1
header: User Manual
footer: asciisplash 1.0.0
date: March 27, 2022
---
## NAME
asciisplash - Launch a fun splashy screen of ASCIImatics animations

## SYNOPSIS
**asciisplash** [-a] [-b] [-C] [-c numcycles] [-d] [-j] [-J] [-m] [-p] [-s song] [-u]

**NOTE:** `asciisplash` can be run by invoking `asciiville [-S] ...`

See `man asciiville` for details on how to front-end `asciisplash` with `asciiville`

## DESCRIPTION
The *asciisplash* command plays one of the ASCIImatics animations included in Asciiville.
It's a fun demonstration of some of the capabilities of the ASCIImatics library. By default,
*asciisplash* will play a series of animations about MusicPlayerPlus. Command line options
can be used to tell *asciisplash* to play animations for the Julia Set or a Plasma animation
as well as play a public domain audio to accompany the ascii art display.

## COMMAND LINE OPTIONS
**-a**
: indicates play audio accompaniment

**-b**
: indicates play alternate audio accompaniment

**-c numcycles**
: specifies the number of times to cycle

**-C**
: indicates use alternate comments in Plasma effect

**-d**
: enabled debug mode

**-J**
: indicates use Julia Set effect and play multiple zooms with different parameters

**-j**
: indicates use Julia Set effect

**-m**
: indicates use MusicPlayerPlus effect

**-p**
: indicates use Plasma effect

**-s song**
: specifies the audio file to use as accompaniment

**-u**
: displays this usage message and exits

Without any options the MusicPlayerPlus effect will repeat

## EXAMPLES
**asciisplash**
: Without options asciisplash will play a series of animations about MusicPlayerPlus. These will repeat until the 'q' key is pressed.

**asciisplash -c 10**
: Plays the MusicPlayerPlus ASCIImatics animations 10 times then exits 

**asciisplash -j -c 5**
: Plays the Julia Set ASCIImatics animation 5 times then exits 

**asciisplash -p**
: Plays the Plasma ASCIImatics animation in an endless loop until the 'q' key is pressed

**asciisplash -p -C**
: Plays the Plasma ASCIImatics animation using alternate comments

**asciisplash -a -c 1**
: Plays the MusicPlayerPlus ASCIImatics animation for one cycle accompanied by a public domain audio

**asciisplash -a -j -s /u/audio/deep.wav**
: Plays the Julia Set ASCIImatics animation and the audio file `/u/audio/deep.wav` as accompaniment

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
ASCIISPLASH is distributed under an Open Source license.
See the file LICENSE in the ASCIISPLASH source distribution
for information on terms &amp; conditions for accessing and
otherwise using ASCIISPLASH and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciijulia**(1), **asciimpplus**(1), **asciiplasma**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

