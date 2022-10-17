---
title: TERMPROFSET
section: 1
header: User Manual
footer: termprofset 1.0.0
date: May 10, 2022
---
## NAME
termprofset - manipulate the profiles of a Gnome or Tilix terminal, or the font setting of an XFCE4 terminal

## SYNOPSIS
**termprofset** [-f fontname] [-s fontsize] [-p profile] [-K socket] [-gklBRStxu]

## DESCRIPTION
The *termprofset* command can be used to set or restore profile settings of a Gnome or Tilix terminal emulator, or the font setting of a Kitty or XFCE4 terminal emulator. Profile settings that can be configured by *termprofset* are:

- font (font name and font size)
- use-system-font
- audible-bell
- use-theme-colors
- background-color
- foreground-color

When setting the profile of a terminal, the following settings are used:

- font 'Monospace 4'
- use-system-font false
- audible-bell false
- use-theme-colors false
- background-color '#000000'
- foreground-color '#AFAFAF'

The font name and font size can be specified on the command line using the `-f fontname` and `-s fontsize` options. Background color and transparency in `xfce4-terminal` can be set with the `-B color` option.

In addition to setting profile settings or font setting, *termprofset* can be used to save or restore profile settings or font setting saved from a previous invocation. Use the `-S` command line option to save the current profile or configuration settings of a terminal emulator. Use the `-R` command line option to indicate restore saved profile settings or font setting. In this way, *termprofset* can be used to manipulate a profile or font temporarily. Display ascii art with a customized profile or font then restore the original profile or font settings.

Current profile or font settings can be listed with the `-l` option.

The `termprofset` command is used by the `show_ascii_art` command when
displaying Ascii Art. During Ascii Art displays the font size is manipulated
to produce higher resolution character graphics during art display while
setting the font size higher for Figlet text display. The font sizes used
in this command can be controlled via the `art_font_size` and `txt_font_size`
values in `$HOME/.config/asciiville/config`. Default font sizes are 4 and 20.

## COMMAND LINE OPTIONS
**-B**
: indicates set background to black, no transparency

**-f 'fontname'**
: specifies the font name to set terminal's font to

**-s 'fontsize'**
: specifies the font size to set terminal's font to

**-p 'profile'**
: specifies the terminal profile to manipulate

**-R**
: indicates restore saved settings

**-S**
: indicates save original settings

**-g**
: indicates use Gnome terminal emulator

**-k**
: indicates use Kitty terminal emulator

**-K 'socket'**
: specifies the socket on which Kitty remote control commands are sent

**-l**
: indicates list current profile settings and exit

**-t**
: indicates use Tilix terminal emulator

**-x**
: indicates use Xfce4 terminal emulator

**-u**
: displays this usage message and exits

Default terminal emulator is Gnome

Default terminal profile is Asciiville

Default font is Monospace

Default font size is 4

## EXAMPLES

**termprofset**
: Without arguments, termprofset sets the Asciiville Gnome profile with a Monospace font and font size 4

**termprofset -t -s 8**
: Sets the Asciiville Tilix profile with a Monospace font and font size 8 

**termprofset -x -s 18**
: Sets the XFCE4 terminal with a Monospace font and font size 18 

**termprofset -R -t**
: Restores the Asciiville Tilix profile with settings saved from a previous run

**termprofset -p default -t -s 18**
: Sets the default Tilix profile with a Monospace font and font size 18 

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
TERMPROFSET is distributed under an Open Source license.
See the file LICENSE in the TERMPROFSET source distribution
for information on terms &amp; conditions for accessing and
otherwise using TERMPROFSET and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1), **show_ascii_art**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

