---
title: SHOE_ASCII_ART
section: 1
header: User Manual
footer: show_ascii_art 1.0.0
date: April 24, 2022
---
## NAME
show_ascii_art - display ascii art

## SYNOPSIS
**show_ascii_art** [-a art[,art2,...]] [-A art_dir] [-b] [-B] [-c] [-C] [-d font_dir] [-D seconds] [-e term] [-E] [-F large_font] [-f small_font] [-g] [-i image] [-I input_dir] [-O output_dir] [-K fifo_name] [-l level] [-L] [-n tabs] [-N depth] [-o] [-p palette] [-P] [-q] [-r] [-R len] [-s show] [-S song] [-t first_text] [-T second_text] [-h height] [-w width] [-W] [-v] [-z] [-Z] [-u]

## DESCRIPTION
The *show_ascii_art* command displays one or more of the ascii art images included in
Asciiville. Command line options can be used to tell *show_ascii_art* to create
a new ascii art image from an image file in any format. Other command line
options can be used to specify the width and heigh of the converted image,
the fonts used to display accompanying text, and the text to display.

The *show_ascii_art* command is not intended as the primary user interface for
ascii art display. Rather, use the *asciiville* command which provides options
for the generation and display of ascii art using *show_ascii_art* as a backend.
See the **asciiville**(1) man page (`man asciiville`).

## COMMAND LINE OPTIONS

**-a 'art'**
: specifies ascii art file(s) to display

    multiple files are separated by a comma with no spaces

        (e.g. `-a Friends/tux,Doctorwhen/Capitola_Village_Vivid`)

    'art' can be the relative path to a file in:

        `/usr/share/asciiville/art/`

    or the path to a file, with or without file extension

**-A 'art_dir'**
: specifies the path to the ascii art folder

**-b**
: when generating ascii art use a border

**-c**
: cycle slideshow endlessly (Ctrl-c to exit show)

**-C**
: center ascii art on screen if border detected

**-d 'font_dir'**
: specifies the path to the figlet fonts

**-D 'seconds'**
: specifies the delay, in seconds, between screens

**-e 'term'**
: specifies the terminal in which execution occurs

    'term' can be one of 'gnome', 'xfce4', or 'tilix'

**-E**
: disables font size changing

**-f 'small_font'**
: specifies the figlet font to use for small text

**-F 'large_font'**
: specifies the figlet font to use for large text

**-g**
: convert image to grayscale

**-i 'image'**
: specifies an image file to convert to ascii art

**-I 'input_dir'**
: generates ascii art from all images in 'input_dir' and saves them in the directory specified with '-O output_dir' (defaults to current directory if '-O output_dir' is specified)

**-K 'fifo_name'**
: use a FIFO to communicate back to caller when done

    Calling process can wait for `show_ascii_art` to exit
    by waiting for 'done' to be written to the FIFO

**-l 'level'**
: use lolcat coloring, 'level' can be '1' or '2' (animate)

**-L**
: lists the ascii art in the 'art_dir' and exits

**-N 'depth'**
: specifies the color depth

    'depth' can be '4' (for ANSI), '8' (for 256 color palette)

    or '24' (for truecolor or 24-bit color)

**-n 'tabs'**
: specifies the number of tabs to indent image display

**-o**
: indicates overwrite any existing ascii art when saving

**-P**
: indicates play audio during slideshow

**-p 'palette'**
: specifies which character set to use for ascii art

    'palette' can be one of 'def', 'long', 'rev', 'longrev'

    'def' is the default set, 'long' a long set,

    'rev' reverses default, 'longrev' reverses long

    Any other argument to '-C' will be taken as the character set

**-q**
: don't display text, just the ascii art

**-r**
: indicates select random fonts

**-R 'len'**
: indicates random slideshow of length 'len' (0 'len' infinite show)

**-S 'song'**
: specifies the song to play as audio track (use default if '-s song' omitted)

**-s 'show'**
: slide show of ascii art

    'show' can be Art, Doctorwhen, Dragonflies, Fractals, Friends, Iterated,
                  Lyapunov, Nature, Owls, Space, Wallpapers, Waterfalls

**-t 'first_text'**
: specifies the first text to display

**-T 'second_text'**
: specifies the second text to display

**-h 'height'**
: specifies the height of the converted ascii art

**-w 'width'**
: specifies the width of the converted ascii art

If only one of 'width' and 'height' is provided, calculate the other from image aspect ratio

**-W**
: indicates do not wait for input to continue viewing ascii art

**-v**
: indicates view ascii art and prompt to continue

**-Z**
: indicates no ANSI escape sequences used in ascii art"

**-z**
: indicates save converted image ascii art in art_dir

**-u**
: displays this usage message and exits

## EXAMPLES
**show_ascii_art**
: Without options show_ascii_art will display an ascii art image and "Welcome to Asciiville" text using Figlet fonts.

**show_ascii_art -C -s Art**
: Display a slide show of Ascii Fine Art, centering the art in the terminal window.

**show_ascii_art -i $HOME/Pictures/selfie.gif**
: Converts the GIF image file `$HOME/Pictures/selfie.gif` to JPEG format using the ImageMagick *convert* utility then generates ascii art from the JPEG file using the Asciiville *jp2a* utility and displays it along with figlet text.

**show_ascii_art -i $HOME/Pictures/profile.jpg -h 20 -r**
: Generates a 20 line ascii art from the JPEG image `$HOME/Pictures/profile.jpg` preserving aspect ratio using the Asciiville *jp2a* utility and displays it along with figlet text using randomly selected fonts.

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
SHOE_ASCII_ART is distributed under an Open Source license.
See the file LICENSE in the SHOE_ASCII_ART source distribution
for information on terms &amp; conditions for accessing and
otherwise using SHOE_ASCII_ART and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciiart**(1), **asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

