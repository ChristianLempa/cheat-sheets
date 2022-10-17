---
title: MPPSPLASH
section: 1
header: User Manual
footer: mppsplash 1.0.0
date: March 27, 2022
---
## NAME
mppsplash - Launch a fun splashy screen of ASCIImatics animations

## SYNOPSIS
**mppsplash** [-a] [-b] [-C] [-c numcycles] [-d] [-j] [-J] [-m] [-p] [-s song] [-u]

**NOTE:** `mppsplash` can be run by invoking `mpplus [-a] [-b] [-jJ] [-m] [-n num] [-N] [-p] [-R] [-S]`

See `man mpplus` for details on how to front-end `mppsplash` with `mpplus`

## DESCRIPTION
The *mppsplash* command plays one of the ASCIImatics animations included in MusicPlayerPlus.
It's a fun demonstration of some of the capabilities of the ASCIImatics library. By default,
*mppsplash* will play a series of animations about MusicPlayerPlus. Command line options
can be used to tell *mppsplash* to play animations for the Julia Set or a Plasma animation
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
**mppsplash**
: Without options mppsplash will play a series of animations about MusicPlayerPlus. These will repeat until the 'q' key is pressed.

**mppsplash -c 10**
: Plays the MusicPlayerPlus ASCIImatics animations 10 times then exits 

**mppsplash -j -c 5**
: Plays the Julia Set ASCIImatics animation 5 times then exits 

**mppsplash -p**
: Plays the Plasma ASCIImatics animation in an endless loop until the 'q' key is pressed

**mppsplash -p -C**
: Plays the Plasma ASCIImatics animation using alternate comments

**mppsplash -a -c 1**
: Plays the MusicPlayerPlus ASCIImatics animation for one cycle accompanied by a public domain audio

**mppsplash -a -j -s /u/audio/deep.wav**
: Plays the Julia Set ASCIImatics animation and the audio file `/u/audio/deep.wav` as accompaniment

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
MPPSPLASH is distributed under an Open Source license.
See the file LICENSE in the MPPSPLASH source distribution
for information on terms &amp; conditions for accessing and
otherwise using MPPSPLASH and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/MusicPlayerPlus/issues

## SEE ALSO
**mpplus**(1), **mpcplus**(1), **mpcpluskeys**(1)

Full documentation and sources at:

https://github.com/doctorfree/MusicPlayerPlus

