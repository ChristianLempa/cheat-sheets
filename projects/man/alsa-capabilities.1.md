---
title: ALSA-CAPABILITIES
section: 1
header: User Manual
footer: alsa-capabilities 2.2.2
date: December 05, 2021
---
## NAME

alsa-capabilities - list alsa audio output interfaces and their capabilities

## SYNOPSIS

**alsa-capabilities** [**-h**, **\--help**]

**alsa-capabilities** [**-s**, **\--samplerates**] ...

## DESCRIPTION

**alsa-capabilities** is a bash (>=4) script that lists the properties
and capabilities of each output interface of each audio device known
by *alsa*. Besides its hardware address, eg
**hw:x,y**, the scripts lists the device and interface names, and
additional details.

## GENERAL OPTIONS

**-h**, **\--help**
:   Display usage information.

**-s**, **\--samplerates**
:   List the samplerates for each encoding format the interface supports.

## FILTER OPTIONS

**-l** *TYPEFILTER*, **\--limit** *TYPEFILTER*
:   Only include interfaces of type *TYPEFILTER*, which can be one of
    **a** (or **analog**),
    **d** (or **digital**), or
    **u** (or **usb**). 

**-c** *REGEXP*, **\--customlimit** *REGEXP*
:   Only include interfaces whose *device name* matches *REGEXP*,
    eg. **"\[Hh\]\[Dd\]\[Mm\]\[Ii\]"**, or **"My Funky Brand"**. 
    
    NOTE: Regular expressions are case sensitive and should be
          surrounded by single or double quotes. The should follow
          Bash-builtin *Pattern Matching* (see below).

**-a** *HWADDRESS*, **\--address** *HWADDRESS*
:   Only include interfaces which have the specified *HWADDRESS*,
    eg. **hw:0,1** means the second interface (`1`) of the first
    device (`0`).

## OUTPUT OPTIONS

**-j**, **\--json** 
:   Prints the results as valid json data for easy parsing by web
    services like REST-api's, or command line parsers, like **jq (1)**.

**-q**, **\--quiet**
:   Surpress listing each interface with its details, ie. only store
    the details of each card in the appropriate bash arrays.

    Besides using the **-q**, **\--quiet** options,
    **alsa-capabilities** was designed to be sourced and used by other
    programs. See README.md for more information.

## CAVEATS

The scripts output is printed to *stdout*; when you want to use the
output in pipes and such, consider using the *OUTPUT OPTIONS* above,
or use:

  **alsa-capabilities 2>&1** | grep ...

## AUTHORS

Written by Ronald van Engelen ronalde@lacocina.nl

Modified and adapted by Ronald Record github@ronrecord.com

## SEE ALSO

**aplay(1)** **alsa-info(1)**

For *REGEXP* rules, see: 
<https://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html>

The **alsa-capabilities** source code and documentation may be downloaded
from <https://gitlab.com/sonida/alsa-capabilities/>.
