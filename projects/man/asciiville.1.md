---
title: ASCIIVILLE
section: 1
header: User Manual
footer: asciiville 1.0.0
date: April 16, 2022
---
## NAME
asciiville - Launch a terminal emulator and specified character based command, ascii art, asciimatics animation, character based Email/FTP/File/Web clients,
and character based utilities

## SYNOPSIS
**asciiville** [-a] [-A] [-b] [-c command] [-C] [-d] [-D delay] [-E len] [-f] [-F] [-g] [-i] [-I] [-jJ] [-kK] [-l] [-L level] [-m] [-M] [-N] [-n num] [-p] [-P script] [-r] [-R] [-s song] [-S] [-t] [-T] [-U] [-v] [-V show] [-w] [-W] [-x] [-X] [-y] [-Y] [-z] [-Z] [-u] [file1 [file2 ...]]

Invoked without any arguments or with the `-i` argument, `asciiville` displays an interactive dialog menu.

## DESCRIPTION
The *asciiville* command acts as a front-end for launching character based utilities and ascii art in various terminal emulators. Asciiville can be used to launch any specified character based command. Command line options also support running the *asciiville* window in a tmux session and recording that session using *asciinema*.

The `asciiville` command can be used to display Ascii Art either as a slideshow or interactively. For example:

```
# Slideshow of Ascii Art in /usr/share/asciiville/art/Art/
asciiville -V Art
# Slideshow of Ascii Art in /usr/share/asciiville/art/Vintage/
asciiville -V Vintage
# Interactive display of Ascii Art in .../file1 and .../file2
asciiville file1 file2 ...
# Slideshow of Ascii Art in file1, file2, and file3
asciiville -V files file1 file2 file3
# Slideshow of Ascii Art files listed in /tmp/asciiart.txt
asciiville -V files=/tmp/asciiart.txt
```

Filenames provided to `asciiville`, either on the command line or in
a specified file, can be absolute paths to files; relative paths to files;
or relative paths to files in the Asciiville Ascii Art galleries folder.
Ascii Art filenames may be provided with or without the filename suffix
(e.g. `Friends/tux.asc` or `Friends/tux.asc.gz` or Friends/tux`).

When provided filename(s) as argument(s) *asciiville* treats the files as
ascii art and displays each file. In slideshow mode the display is paused
for a configurable number of seconds between ascii art files. In interactive
mode the display waits for the user to type 'Enter' before displaying the next
file. In this mode, if the user types 'z' or 'b' followed by 'Enter' then
*asciiville* enters "zoom/browse" mode. In zoom/browse mode the user
can zoom in and out of the ascii art. Use the following key presses to
navigate in zoom/browse mode:

- 'i' zoom in
- 'j' zoom in more
- 'n' zoom in even more
- 'o' zoom out
- 'k' zoom out more
- 'm' zoom out even more
- 'r' restore to original
- 'h' display a help message
- 'q' or 'x' to exit zoom/browse mode

In addition, in interactive mode the user can enter 's' or 'S' followed
by 'Return' to enter info "slideshow" mode. In slideshow mode the ascii art
is displayed for a few seconds then the next file is displayed. No user
interaction is possible during slideshow mode other than 'Ctrl-c' to exit.

The *asciiville* command can also act as a front-end to the *asciisplash* and *asciisplash-tmux* commands when invoked with the `-S` and `-T` command line options.

When invoked with the `-i` option, `asciiville` presents a selection menu and operates in interactive mode. Included in the wide variety of options available in the Asciiville interactive menus are selections to display the *MusicPlayerPlus* and *RoonCommandLine* interactive menus.

The interactive menu interface provides three types of menu options. Some menu selections trigger the execution of a command. Other menu selections are used to set the command that would be run when a terminal emulator is selected. Finally, some menu selections can be used to toggle preferences like *Fullscreen*, *Use Tmux*, and *Record Tmux Session*. Once a command and terminal type have been selected and desired options are set then the command can be executed by selecting the menu entry *Run <command> in <terminal name> Terminal*.

Previously started tmux sessions and asciimatics scripts can be quickly and easily terminated by executing the `asciiville -K` command.

Asciiville preferences are maintained in `$HOME/.config/asciiville/config`. Preferences set in interactive menu mode are preserved over invocations of `asciiville`. For example, if a command and terminal were selected in interactive menu mode then those selections will automatically be applied the next time `asciiville` is run.

## CONFIGURATION

The `asciiville` command initializes some configuration settings by reading the file `$HOME/.config/asciiville/config`. These are user configurable and saved each time the `asciiville` command exits. A sample Asciiville configuration file is provided below. In this sample configuration the *ARTDIR* is set to `/usr/share/asciiville/art`, the default Asciiville Ascii Art galleries folder. To change the Ascii Art galleries folder, modify this setting. For example, to change where `asciiville` looks for Ascii Art galleries, this setting could be modified to:

```
ARTDIR=${HOME}/Pictures/AsciiArt
```

Asciiville commands would then look in `$HOME/Pictures/AsciiArt` for Ascii Art galleries rather than `/usr/share/asciiville/art`.

Of particular interest are the `art_font_size` and `txt_font_size` configuration settings. These control the size of the font used to display Ascii Art slideshows and the Figlet text in slideshows.  Individual display devices differ in resolution. Terminal emulator windows used for display of Ascii Art vary in number of rows and columns available. The Ascii Art included with Asciiville was generated in fairly high resolution. Reducing the `art_font_size` will decrease the amount of screen the art display requires while increasing that font size will increase the size of the art displayed. Similarly, decreasing or increasing the `txt_font_size` will shrink or enlargen the Figlet text displayed.  The default settings for these two configuration parameters are '4' and '20'. If the art displayed during a slideshow is too small or you wish to make it larger, change `art_font_size=4` to `art_font_size=6` and `txt_font_size=20` to `txt_font_size=24`. Some experimentation may be required to fit the art to your display and terminal emulator window.

A sample Asciiville configuration file `$HOME/.config/asciiville/config`:

```
ARTDIR=/usr/share/asciiville/art
MUSEDIR=/usr/share/asciiville/music
SONG=/home/ronnie/Music/Buckingham_Green.mp3
ALTSONG=/Epic_Dramatic-Yuriy_Bespalov.wav
AUDIO=1
BROWSER=w3m
COMMAND=newsboat
FULLSCREEN=
LOLCAT="lolcat"
MTITLE="RSS Feeds"
CURRENT=
GNOME=1
RETRO=
TILIX=
XFCE4=

use_lolcat=1
use_lol=YES
journal="asciiville"
style="fancy"
art_font_size=6
txt_font_size=24

defchars='   ...,;:clodxkO0KXNWM'
revchars='MWNXK0Okxdolc:;,...   '
revlong='WMZO0QLCJUYXzcvun1il;:,^.. '
longchars=' ..^,:;li1nuvczXYUJCLQ0OZMW'
```

## SELECTING FILES AND FOLDERS

In interactive menu mode, **asciiville** may prompt for the selection of ascii art file(s) and folders. The **asciiville** command utilizes the **ranger** file manager command for file and folder selection.

Choosing a directory in Ranger is done by visiting a directory. Use the arrow keys to browse folders. Press 'Enter' to enter a directory. Create a new directory with `:mkdir <dirname>`. While in the directory you wish to select, quit Ranger with 'q'.

Choosing a file in Ranger is done by visiting a directory and selecting a file. Use the arrow keys to browse folders. Press 'Enter' or 'Right Arrow' to enter a directory and 'Left Arrow' to go back up a directory. While in a directory, use the arrow keys to navigate to the file you wish to select. To select a single file, press 'Enter' when the file is highlighted. To select multiple files, press 'Space' and navigate to another file. All files selected with 'Space' will be added to your selections when you press 'Enter' on a selected file to complete the selection process.

## COMMAND LINE OPTIONS

*Terminal/Command options:*

**-c 'command'**
: Indicates run 'command' in selected terminal window. If *command* is one of the special keywords (*endo*, *maps*, *moon*, *news*, *reddit*, *search*, *speed*, *translate*, *twitter*, *weather*) then display fluid dynamics simulations, a map, the phase of the Moon, run the `newsboat` RSS feed reader, perform a web search, perform a speed test, run the `got` text based translation tool, run the command line twitter client, or display a weather report.

**-d**
: Indicates use disk usage analyzer as command

**-f**
: Indicates fullscreen display

**-g**
: Indicates use gnome terminal emulator

**-i**
: Indicates start asciiville in interactive mode

**-I**
: Indicates display system info

**-k**
: Indicates use kitty terminal emulator

**-l**
: Indicates use lynx as the default command

**-L 'level'**
: Use lolcat coloring, 'level' can be '1' or '2' (animate)

**-r**
: Indicates use retro terminal emulator

**-t**
: Indicates use tilix terminal emulator

**-U**
: Indicates set command to Ninvaders

**-w**
: Indicates use w3m web browser as the default command

**-W**
: Indicates use cmatrix as the default command

**-x**
: Indicates use xfce4 terminal emulator

**-X**
: Indicates use current terminal emulator window

**-y**
: Indicates use ranger file manager as the default command

**-Y**
: Indicates use NetHack dungeon game as the default command

**-z**
: Indicates use neomutt email client as the default command

*Slideshow / ASCIImatics animation options:*

**-a**
: Indicates play audio during display

**-A**
: Indicates use Asciiville scenes in ASCIImatics display

**-b**
: Indicates use backup audio during display

**-C**
: Indicates cycle slideshow endlessly (Ctrl-c to exit show)

**-D 'delay'**
: Specifies delay, in seconds, between art display (default 5)

**-E 'len'**
: Indicates random slideshow of length 'len' (0 infinite)

**-j**
: Indicates use Julia Set scenes in ASCIImatics display

**-J**
: Indicates Julia Set with several runs using different parameters

**-m**
: Indicates use MusicPlayerPlus scenes in ASCIImatics display

**-M**
: Indicates use the MusicPlayerPlus `mpcplus` music player client

**-n num**
: Specifies the number of times to cycle ASCIImatics scenes

**-N**
: Indicates use alternate comments in Plasma ASCIImatics scenes

**-p**
: Indicates use Plasma scenes in ASCIImatics display

**-P script**
: Specifies the ASCIImatics script to run

**-s song**
: Specifies a song to accompany an ASCIImatics animation

**-S**
: Indicates display ASCIImatics splash animation

**-V 'show'**
: Displays an ascii art slide show

    'show' can be one of 'Art', 'Doctorwhen', 'Dragonflies', 'Fractals', 'Friends', 'Iterated', 'Lyapunov', 'Nature', 'Owls', 'Space', 'Vintage', 'Wallpapers', 'Waterfalls', the name of a custom ascii art folder, the slideshow keyword 'files' which indicates display a slideshow using the ascii art files provided on the command line, or the slideshow argument 'files=/path/to/file' which indicates read the list of slideshow files from the file '/path/to/file'

**-Z**
: Indicates do not play audio during slideshow/animation

*General options:*

**-K**
: Indicates kill Asciiville tmux sessions and ASCIImatics scripts

**-R**
: Indicates record tmux session with asciinema

**-T**
: Indicates use a tmux session for either ASCIImatics or command

**-v**
: Displays the Asciiville version and exits

**-u**
: Displays this usage message and exits

Remaining arguments are filenames of ascii art to display

Ascii art filenames can be relative to the Ascii Art Gallery folder
and need not specify the filename suffix. For example:

**asciiville -L 2 Friends/tux Doctorwhen/Capitola_Village_Vivid**

Invoked without any arguments, **asciiville** will display an interactive menu

## EXAMPLES
**asciiville**
: Launches `asciiville` in interactive mode with menu selections controlling actions rather than command line arguments, Btop System Monitor is the default command

**asciiville -E 25**
: Displays a random slideshow of 25 ascii art images selected from all the galleries and displayed in the current terminal window, console, or terminal emulator specified in `$HOME/.config/asciiville/config`

**asciiville -E 30 -V Vintage -D 10 -t**
: Displays a random slideshow of 30 ascii art images selected from the Vintage art gallery in a Tilix terminal window with a delay of 10 seconds between images

**asciiville -i -y**
: Launches `asciiville` in interactive mode with Ranger File Manager selected as command rather than Btop System Monitor

**asciiville -r -y**
: Launches `ranger` file manager running in cool-retro-term terminal emulator

**asciiville -M -t**
: Launches `mpcplus` music player running in Tilix terminal emulator

**asciiville -c endo**
: Displays a series of ascii fluid dyanamics simulations using `endoh1`

**asciiville -c maps**
: Displays a zoomable map of the world using `mapscii`

**asciiville -c moon**
: Displays the Phase of the Moon using `wttr.in`

**asciiville -c news**
: Launches the `newsboat` text based RSS feed reader in the current terminal

**asciiville -c reddit**
: Launches the `tuir` text based Reddit UI in the current terminal

**asciiville -c search**
: Launches the `ddgr` command line web search in the current terminal window

**asciiville -c translate**
: Launches the `got` command line translation tool in the current terminal window

**asciiville -c twitter**
: Launches the `rainbowstream` command line Twitter client in the current terminal window

**asciiville -c weather**
: Displays a weather report for your IP address location using `wttr.in`

**asciiville -c cmus -g**
: Launches the `cmus` music player client running in a gnome-terminal emulator window

**asciiville -f -t -z**
: Launches `neomutt` mail client in fullscreen mode running in a tilix terminal emulator window

**asciiville -l -T -x**
: Launches `lynx` web browser running in a tmux session in an xfce4-terminal window

**asciiville -R -T**
: Creates an asciinema recording of `btop` system monitor running in a tmux session

**asciiville -S -j -a**
: Launch `asciisplash` displaying the Julia Set asciimatics animation with audio

## AUTHORS
Written by Ronald Record github@ronrecord.com

## LICENSING
ASCIIVILLE is distributed under an Open Source license.
See the file LICENSE in the ASCIIVILLE source distribution
for information on terms &amp; conditions for accessing and
otherwise using ASCIIVILLE and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciiart**(1), **asciijulia**(1), **asciimpplus**(1), **asciinema**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **btop**(1), **cbftp**(1), **ddgr**(1), **jp2a**(1), **lynx**(1), **mutt**(1), **ranger**(1), **show_moon**(1), **show_weather**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville

