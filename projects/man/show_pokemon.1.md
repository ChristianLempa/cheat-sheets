---
title: SHOW_POKEMON
section: 1
header: User Manual
footer: show_pokemon 1.0.0
date: September 29, 2022
---
## NAME
show_pokemon - Display a Pokemon pocket monster

## SYNOPSIS
**show_pokemon** [-i id] [-n name] [-u]

## DESCRIPTION
The *show_pokemon* command displays a Pokemon pocket monster.
Command line options can be used to specify the Pokemon ID or name to retrieve.
If no ID or name is given on the command line then a random Pokemon is displayed.

## COMMAND LINE OPTIONS

**-i 'id'**
: specifies the Pokemon ID to retrieve

**-n 'name'**
: specifies the Pokemon name to retrieve

**-u**
: indicates show this usage message and exit

## EXAMPLES
**show_pokemon**
: Without options show_pokemon will display a randomly selected Pokemon

**show_pokemon -i 543**
: Display the Pokemon with ID 343. ID range is 1-905.

**show_pokemon -n Overqwil**
: Display the Pokemon with name 'Overqwil'. Names can be specified in upper or lower case.

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
SHOW_POKEMON is distributed under an Open Source license.
See the file LICENSE in the SHOW_POKEMON source distribution
for information on terms &amp; conditions for accessing and
otherwise using SHOW_POKEMON and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**show_moon**(1), **show_weather**(1), **asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

