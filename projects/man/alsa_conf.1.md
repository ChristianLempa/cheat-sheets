---
title: ALSA_CONF
section: 1
header: User Manual
footer: alsa_conf 2.7
date: December 07, 2021
---
## NAME
**alsa_conf** - Set/get the ALSA sound configuration

## SYNOPSIS
**alsa_conf** [-c] [-e] [-l] [-n] [-o outfile] [-q] [-r] [-t template] [-u]

## DESCRIPTION
The *alsa_conf* command can be used to interactively set the ALSA sound configuration in */etc/asound.conf* at the command line.

## COMMAND LINE OPTIONS
**-u**
: Display usage message

**-c**
: Indicates perform a check and notify if update needed

**-e**
: Indicates perform an update of */etc/asound.conf*

**-l**
: Indicates list audio input/output configured devices

**-n**
: Indicates non-interactive execution (guess at settings)

**-o outfile**
: 'outfile' specifies an alternate output file for generated asound.conf

**-q**
: Indicates quiet execution

**-r**
: Indicates restore original */etc/asound.conf*

**-t template**
: 'template' specifies an alternate *asound.conf* template to use

Default generated output is the file */etc/asound.conf*

Default asound.conf template can be found in:

	*/usr/share/musicplayerplus/asound.conf.tmpl*

## EXAMPLES
**alsa_conf -c -q**
: Quietly check the */etc/asound.conf* configuration and exit with status

**alsa_conf -e**
: Display an interactive menu to allow selection of audio input and output
devices and update the */etc/asound.conf* configuration

## AUTHORS
Written by Ronald Record &lt;github@ronrecord.com&gt;

## LICENSING
ALSA_CONF is distributed under an Open Source license.
See the file LICENSE in the ALSA_CONF source distribution
for information on terms &amp; conditions for accessing and
otherwise using ALSA_CONF and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at: &lt;https://github.com/doctorfree/MusicPlayerPlus/issues&gt;

## SEE ALSO
**mpplus**(1)

Full documentation and sources at: &lt;https://github.com/doctorfree/MusicPlayerPlus&gt;

