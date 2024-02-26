# Terminal Escape Code Cheatsheet

A list of commonly used escape codes in terminal emulators.

## Table Of Contents

- [ANSI Escape Sequences](#ansi-escape-sequences)
- [Sequences](#sequences)
- [General ASCII Codes](#general-ascii-codes)
- [Cursor Controls](#cursor-controls)
- [Erase Functions](#erase-functions)
- [Colors / Graphics Mode](#colors-graphics-mode)
- [Screen Modes](#screen-modes)
- [Control Escape Codes](#control-escape-codes)
- [8 Color Escape Codes](#8-color-escape-codes)
- [256 Color Escape Codes](#256-color-escape-codes)
- [True Color](#true-color)
- [See also](#see-also)
- [Resources](#resources)

## ANSI Escape Sequences

Standard escape codes are prefixed with `Escape`:

- Ctrl-Key: `^[`
- Octal: `\033`
- Unicode: `\u001b`
- Hexadecimal: `\x1B`
- Decimal: `27`

Followed by the command, somtimes delimited by opening square bracket (`[`), known as a Control Sequence Introducer (CSI), optionally followed by arguments and the command itself.

Arguments are delimeted by semi colon (`;`).

For example:

```sh
\x1b[1;31m  # Set style to bold, red foreground.
```

## Sequences

- `ESC` - sequence starting with `ESC` (`\x1B`)
- `CSI` - Control Sequence Introducer: sequence starting with `ESC [` or CSI (`\x9B`)
- `DCS` - Device Control String: sequence starting with `ESC P` or DCS (`\x90`)
- `OSC` - Operating System Command: sequence starting with `ESC ]` or OSC (`\x9D`)

Any whitespaces between sequences and arguments should be ignored. They are present for improved readability.

## General ASCII Codes

| **Name** | **decimal** | **octal** | **hex** | **C-escape** | **Ctrl-Key** | **Description** |
| ----- | ------- | ----- | ---- | -------- | -------- | ------------------------------ |
| `BEL` | 7       | 007   | 0x07 | `\a`     | `^G`     | Terminal bell                  |
| `BS`  | 8       | 010   | 0x08 | `\b`     | `^H`     | Backspace                      |
| `HT`  | 9       | 011   | 0x09 | `\t`     | `^I`     | Horizontal TAB                 |
| `LF`  | 10      | 012   | 0x0A | `\n`     | `^J`     | Linefeed (newline)             |
| `VT`  | 11      | 013   | 0x0B | `\v`     | `^K`     | Vertical TAB                   |
| `FF`  | 12      | 014   | 0x0C | `\f`     | `^L`     | Formfeed (also: New page `NP`) |
| `CR`  | 13      | 015   | 0x0D | `\r`     | `^M`     | Carriage return                |
| `ESC` | 27      | 033   | 0x1B | `\e`[\*](#escape) | `^[` | Escape character           |
| `DEL` | 127     | 177   | 0x7F | `<none>` | `<none>` | Delete character               |

<div id="escape"></div>

> **Note:** Some control escape sequences, like `\e` for `ESC`, are not guaranteed to work in all languages and compilers. It is recommended to use the decimal, octal or hex representation as escape code.

  

> **Note:** The **Ctrl-Key** representation is simply associating the non-printable characters from ASCII code 1 with the printable (letter) characters from ASCII code 65 ("A"). ASCII code 1 would be `^A` (Ctrl-A), while ASCII code 7 (BEL) would be `^G` (Ctrl-G). This is a common representation (and input method) and historically comes from one of the VT series of terminals.

## Cursor Controls

| **ESC Code Sequence** | **Description** |
| :-------------------- | :-------------- |
| `ESC[H`                                            | moves cursor to home position (0, 0)                     |
| `ESC[{line};{column}H` <br> `ESC[{line};{column}f` | moves cursor to line #, column #                         |
| `ESC[#A`                                           | moves cursor up # lines                                  |
| `ESC[#B`                                           | moves cursor down # lines                                |
| `ESC[#C`                                           | moves cursor right # columns                             |
| `ESC[#D`                                           | moves cursor left # columns                              |
| `ESC[#E`                                           | moves cursor to beginning of next line, # lines down     |
| `ESC[#F`                                           | moves cursor to beginning of previous line, # lines up   |
| `ESC[#G`                                           | moves cursor to column #                                 |
| `ESC[6n`                                           | request cursor position (reports as `ESC[#;#R`)          |
| `ESC M`                                            | moves cursor one line up, scrolling if needed            |
| `ESC 7`                                            | save cursor position (DEC)                               |
| `ESC 8`                                            | restores the cursor to the last saved position (DEC)     |
| `ESC[s`                                            | save cursor position (SCO)                               |
| `ESC[u`                                            | restores the cursor to the last saved position (SCO)     |

> **Note:** Some sequences, like saving and restoring cursors, are private sequences and are not standardized. While some terminal emulators (i.e. xterm and derived) support both SCO and DEC sequences, they are likely to have different functionality. It is therefore recommended to use DEC sequences.

## Erase Functions

| **ESC Code Sequence** | **Description** |
| :-------------------- | :-------------- |
| `ESC[J`           | erase in display (same as ESC\[0J)        |
| `ESC[0J`          | erase from cursor until end of screen     |
| `ESC[1J`          | erase from cursor to beginning of screen  |
| `ESC[2J`          | erase entire screen                       |
| `ESC[3J`          | erase saved lines                         |
| `ESC[K`           | erase in line (same as ESC\[0K)           |
| `ESC[0K`          | erase from cursor to end of line          |
| `ESC[1K`          | erase start of line to the cursor         |
| `ESC[2K`          | erase the entire line                     |

> Note: Erasing the line won't move the cursor, meaning that the cursor will stay at the last position it was at before the line was erased. You can use `\r` after erasing the line, to return the cursor to the start of the current line.

## Colors / Graphics Mode

| **ESC Code Sequence** | **Reset Sequence** | **Description** |
| :-------------------- | :----------------- | :-------------- |
| `ESC[1;34;{...}m` |                | Set graphics modes for cell, separated by semicolon (`;`). |
| `ESC[0m`          |                | reset all modes (styles and colors)                        |
| `ESC[1m`          | `ESC[22m`      | set bold mode.                                             |
| `ESC[2m`          | `ESC[22m`      | set dim/faint mode.                                        |
| `ESC[3m`          | `ESC[23m`      | set italic mode.                                           |
| `ESC[4m`          | `ESC[24m`      | set underline mode.                                        |
| `ESC[5m`          | `ESC[25m`      | set blinking mode                                          |
| `ESC[7m`          | `ESC[27m`      | set inverse/reverse mode                                   |
| `ESC[8m`          | `ESC[28m`      | set hidden/invisible mode                                  |
| `ESC[9m`          | `ESC[29m`      | set strikethrough mode.                                    |

> **Note:** Some terminals may not support some of the graphic mode sequences listed above.

> **Note:** Both dim and bold modes are reset with the `ESC[22m` sequence. The `ESC[21m` sequence is a non-specified sequence for double underline mode and only work in some terminals and is reset with `ESC[24m`.

### Color codes

Most terminals support 8 and 16 colors, as well as 256 (8-bit) colors. These colors are set by the user, but have commonly defined meanings.

#### 8-16 Colors

| **Color Name** | **Foreground Color Code** | **Background Color Code** |
| :------------- | :------------------------ | :------------------------ |
| Black      | `30`                  | `40`                  |
| Red        | `31`                  | `41`                  |
| Green      | `32`                  | `42`                  |
| Yellow     | `33`                  | `43`                  |
| Blue       | `34`                  | `44`                  |
| Magenta    | `35`                  | `45`                  |
| Cyan       | `36`                  | `46`                  |
| White      | `37`                  | `47`                  |
| Default    | `39`                  | `49`                  |
| Reset      | `0`                   | `0`                   |

> **Note:** the _Reset_ color is the reset code that resets _all_ colors and text effects, Use _Default_ color to reset colors only.

Most terminals, apart from the basic set of 8 colors, also support the "bright" or "bold" colors. These have their own set of codes, mirroring the normal colors, but with an additional `;1` in their codes:

```sh
# Set style to bold, red foreground.
\x1b[1;31mHello
# Set style to dimmed white foreground with red background.
\x1b[2;37;41mWorld
```

Terminals that support the [aixterm specification](https://sites.ualberta.ca/dept/chemeng/AIX-43/share/man/info/C/a_doc_lib/cmds/aixcmds1/aixterm.htm) provides bright versions of the ISO colors, without the need to use the bold modifier:

| **Color Name** | **Foreground Color Code** | **Background Color Code** |
| :------------- | :------------------------ | :------------------------ |
| Bright Black   | `90`                  | `100`                 |
| Bright Red     | `91`                  | `101`                 |
| Bright Green   | `92`                  | `102`                 |
| Bright Yellow  | `93`                  | `103`                 |
| Bright Blue    | `94`                  | `104`                 |
| Bright Magenta | `95`                  | `105`                 |
| Bright Cyan    | `96`                  | `106`                 |
| Bright White   | `97`                  | `107`                 |

#### 256 Colors

The following escape codes tells the terminal to use the given color ID:

| **ESC Code Sequence** | **Description** |
| :-------------------- | :-------------- |
| `ESC[38;5;{ID}m` | Set foreground color. |
| `ESC[48;5;{ID}m` | Set background color. |

Where `{ID}` should be replaced with the color index from 0 to 255 of the following color table:

![256 Color table](https://user-images.githubusercontent.com/995050/47952855-ecb12480-df75-11e8-89d4-ac26c50e80b9.png)

The table starts with the original 16 colors (0-15).

The proceeding 216 colors (16-231) or formed by a 3bpc RGB value offset by 16, packed into a single value.

The final 24 colors (232-255) are grayscale starting from a shade slighly lighter than black, ranging up to shade slightly darker than white.

Some emulators interpret these steps as linear increments (`256 / 24`) on all three channels, although some emulators may explicitly define these values.

#### RGB Colors

More modern terminals supports [Truecolor](https://en.wikipedia.org/wiki/Color_depth#True_color_.2824-bit.29) (24-bit RGB), which allows you to set foreground and background colors using RGB.

These escape sequences are usually not well documented.

| **ESC Code Sequence** | **Description** |
| :-------------------- | :-------------- |
| `ESC[38;2;{r};{g};{b}m` | Set foreground color as RGB. |
| `ESC[48;2;{r};{g};{b}m` | Set background color as RGB. |

> Note that `;38` and `;48` corresponds to the 16 color sequence and is interpreted by the terminal to set the foreground and background color respectively. Where as `;2` and `;5` sets the color format.

## Screen Modes

### Set Mode

| **ESC Code Sequence** | **Description** |
| :-------------------- | :-------------- |
| `ESC[={value}h`   | Changes the screen width or type to the mode specified by value.                                                                                                      |
| `ESC[=0h`         | 40 x 25 monochrome (text)                                                                                                                                             |
| `ESC[=1h`         | 40 x 25 color (text)                                                                                                                                                  |
| `ESC[=2h`         | 80 x 25 monochrome (text)                                                                                                                                             |
| `ESC[=3h`         | 80 x 25 color (text)                                                                                                                                                  |
| `ESC[=4h`         | 320 x 200 4-color (graphics)                                                                                                                                          |
| `ESC[=5h`         | 320 x 200 monochrome (graphics)                                                                                                                                       |
| `ESC[=6h`         | 640 x 200 monochrome (graphics)                                                                                                                                       |
| `ESC[=7h`         | Enables line wrapping                                                                                                                                                 |
| `ESC[=13h`        | 320 x 200 color (graphics)                                                                                                                                            |
| `ESC[=14h`        | 640 x 200 color (16-color graphics)                                                                                                                                   |
| `ESC[=15h`        | 640 x 350 monochrome (2-color graphics)                                                                                                                               |
| `ESC[=16h`        | 640 x 350 color (16-color graphics)                                                                                                                                   |
| `ESC[=17h`        | 640 x 480 monochrome (2-color graphics)                                                                                                                               |
| `ESC[=18h`        | 640 x 480 color (16-color graphics)                                                                                                                                   |
| `ESC[=19h`        | 320 x 200 color (256-color graphics)                                                                                                                                  |
| `ESC[={value}l`   | Resets the mode by using the same values that Set Mode uses, except for 7, which disables line wrapping. The last character in this escape sequence is a lowercase L. |

### Common Private Modes

These are some examples of private modes, which are not defined by the specification, but are implemented in most terminals.

| **ESC Code Sequence** | **Description** |
| :-------------------- | :-------------- |
| `ESC[?25l`        | make cursor invisible           |
| `ESC[?25h`        | make cursor visible             |
| `ESC[?47l`        | restore screen                  |
| `ESC[?47h`        | save screen                     |
| `ESC[?1049h`      | enables the alternative buffer  |
| `ESC[?1049l`      | disables the alternative buffer |

Refer to the [XTerm Control Sequences](https://invisible-island.net/xterm/ctlseqs/ctlseqs.html) for a more in-depth list of private modes defined by XTerm.

> Note: While these modes may be supported by the most terminals, some may not work in multiplexers like tmux.

### Keyboard Strings

```sh
ESC[{code};{string};{...}p
```

Redefines a keyboard key to a specified string.

The parameters for this escape sequence are defined as follows:

- `code` is one or more of the values listed in the following table. These values represent keyboard keys and key combinations. When using these values in a command, you must type the semicolons shown in this table in addition to the semicolons required by the escape sequence. The codes in parentheses are not available on some keyboards. `ANSI.SYS` will not interpret the codes in parentheses for those keyboards unless you specify the `/X` switch in the `DEVICE` command for `ANSI.SYS`.

- `string` is either the ASCII code for a single character or a string contained in quotation marks. For example, both 65 and "A" can be used to represent an uppercase A.

> **IMPORTANT:** Some of the values in the following table are not valid for all computers. Check your computer's documentation for values that are different.

#### List of keyboard strings

| **Key** | **Code** | **SHIFT+code** | **CTRL+code** | **ALT+code**  |
| ------- | -------- | -------------- | ------------- | ------------- |
| F1                       | 0;59     | 0;84       | 0;94      | 0;104     |
| F2                       | 0;60     | 0;85       | 0;95      | 0;105     |
| F3                       | 0;61     | 0;86       | 0;96      | 0;106     |
| F4                       | 0;62     | 0;87       | 0;97      | 0;107     |
| F5                       | 0;63     | 0;88       | 0;98      | 0;108     |
| F6                       | 0;64     | 0;89       | 0;99      | 0;109     |
| F7                       | 0;65     | 0;90       | 0;100     | 0;110     |
| F8                       | 0;66     | 0;91       | 0;101     | 0;111     |
| F9                       | 0;67     | 0;92       | 0;102     | 0;112     |
| F10                      | 0;68     | 0;93       | 0;103     | 0;113     |
| F11                      | 0;133    | 0;135      | 0;137     | 0;139     |
| F12                      | 0;134    | 0;136      | 0;138     | 0;140     |
| HOME (num keypad)        | 0;71     | 55         | 0;119     | \--       |
| UP ARROW (num keypad)    | 0;72     | 56         | (0;141)   | \--       |
| PAGE UP (num keypad)     | 0;73     | 57         | 0;132     | \--       |
| LEFT ARROW (num keypad)  | 0;75     | 52         | 0;115     | \--       |
| RIGHT ARROW (num keypad) | 0;77     | 54         | 0;116     | \--       |
| END (num keypad)         | 0;79     | 49         | 0;117     | \--       |
| DOWN ARROW (num keypad)  | 0;80     | 50         | (0;145)   | \--       |
| PAGE DOWN (num keypad)   | 0;81     | 51         | 0;118     | \--       |
| INSERT (num keypad)      | 0;82     | 48         | (0;146)   | \--       |
| DELETE (num keypad)      | 0;83     | 46         | (0;147)   | \--       |
| HOME                     | (224;71) | (224;71)   | (224;119) | (224;151) |
| UP ARROW                 | (224;72) | (224;72)   | (224;141) | (224;152) |
| PAGE UP                  | (224;73) | (224;73)   | (224;132) | (224;153) |
| LEFT ARROW               | (224;75) | (224;75)   | (224;115) | (224;155) |
| RIGHT ARROW              | (224;77) | (224;77)   | (224;116) | (224;157) |
| END                      | (224;79) | (224;79)   | (224;117) | (224;159) |
| DOWN ARROW               | (224;80) | (224;80)   | (224;145) | (224;154) |
| PAGE DOWN                | (224;81) | (224;81)   | (224;118) | (224;161) |
| INSERT                   | (224;82) | (224;82)   | (224;146) | (224;162) |
| DELETE                   | (224;83) | (224;83)   | (224;147) | (224;163) |
| PRINT SCREEN             | \--      | \--        | 0;114     | \--       |
| PAUSE/BREAK              | \--      | \--        | 0;0       | \--       |
| BACKSPACE                | 8        | 8          | 127       | (0)       |
| ENTER                    | 13       | \--        | 10        | (0        |
| TAB                      | 9        | 0;15       | (0;148)   | (0;165)   |
| NULL                     | 0;3      | \--        | \--       | \--       |
| A                        | 97       | 65         | 1         | 0;30      |
| B                        | 98       | 66         | 2         | 0;48      |
| C                        | 99       | 66         | 3         | 0;46      |
| D                        | 100      | 68         | 4         | 0;32      |
| E                        | 101      | 69         | 5         | 0;18      |
| F                        | 102      | 70         | 6         | 0;33      |
| G                        | 103      | 71         | 7         | 0;34      |
| H                        | 104      | 72         | 8         | 0;35      |
| I                        | 105      | 73         | 9         | 0;23      |
| J                        | 106      | 74         | 10        | 0;36      |
| K                        | 107      | 75         | 11        | 0;37      |
| L                        | 108      | 76         | 12        | 0;38      |
| M                        | 109      | 77         | 13        | 0;50      |
| N                        | 110      | 78         | 14        | 0;49      |
| O                        | 111      | 79         | 15        | 0;24      |
| P                        | 112      | 80         | 16        | 0;25      |
| Q                        | 113      | 81         | 17        | 0;16      |
| R                        | 114      | 82         | 18        | 0;19      |
| S                        | 115      | 83         | 19        | 0;31      |
| T                        | 116      | 84         | 20        | 0;20      |
| U                        | 117      | 85         | 21        | 0;22      |
| V                        | 118      | 86         | 22        | 0;47      |
| W                        | 119      | 87         | 23        | 0;17      |
| X                        | 120      | 88         | 24        | 0;45      |
| Y                        | 121      | 89         | 25        | 0;21      |
| Z                        | 122      | 90         | 26        | 0;44      |
| 1                        | 49       | 33         | \--       | 0;120     |
| 2                        | 50       | 64         | 0         | 0;121     |
| 3                        | 51       | 35         | \--       | 0;122     |
| 4                        | 52       | 36         | \--       | 0;123     |
| 5                        | 53       | 37         | \--       | 0;124     |
| 6                        | 54       | 94         | 30        | 0;125     |
| 7                        | 55       | 38         | \--       | 0;126     |
| 8                        | 56       | 42         | \--       | 0;126     |
| 9                        | 57       | 40         | \--       | 0;127     |
| 0                        | 48       | 41         | \--       | 0;129     |
| \-                       | 45       | 95         | 31        | 0;130     |
| \=                       | 61       | 43         | \---      | 0;131     |
| \[                       | 91       | 123        | 27        | 0;26      |
| \]                       | 93       | 125        | 29        | 0;27      |
|                          | 92       | 124        | 28        | 0;43      |
| ;                        | 59       | 58         | \--       | 0;39      |
| '                        | 39       | 34         | \--       | 0;40      |
| ,                        | 44       | 60         | \--       | 0;51      |
| .                        | 46       | 62         | \--       | 0;52      |
| /                        | 47       | 63         | \--       | 0;53      |
| \`                       | 96       | 126        | \--       | (0;41)    |
| ENTER (keypad)           | 13       | \--        | 10        | (0;166)   |
| / (keypad)               | 47       | 47         | (0;142)   | (0;74)    |
| \* (keypad)              | 42       | (0;144)    | (0;78)    | \--       |
| \- (keypad)              | 45       | 45         | (0;149)   | (0;164)   |
| \+ (keypad)              | 43       | 43         | (0;150)   | (0;55)    |
| 5 (keypad)               | (0;76)   | 53         | (0;143)   | \--       |

## Control Escape Codes

| **Key Name** | **Escape Code** | | **Key Name** | **Escape Code** |
| --- | --- |-| --- | --- |
| S-up | `x1b[1;2A` | | S-down | `x1b[1;2B` |
| S-right | `x1b[1;2C` | | S-left | `x1b[1;2D` |
| S-end | `x1b[1;2F` | | S-home | `x1b[1;2H` |
| M-up | `x1b[1;3A` | | M-down | `x1b[1;3B` |
| M-right | `x1b[1;3C` | | M-left | `x1b[1;3D` |
| M-end | `x1b[1;3F` | | M-home | `x1b[1;3H` |
| M-S-up | `x1b[1;4A` | | M-S-down | `x1b[1;4B` |
| M-S-right | `x1b[1;4C` | | M-S-left | `x1b[1;4D` |
| M-S-end | `x1b[1;4F` | | M-S-home | `x1b[1;4H` |
| C-up | `x1b[1;5A` | | C-down | `x1b[1;5B` |
| C-right | `x1b[1;5C` | | C-left | `x1b[1;5D` |
| C-end | `x1b[1;5F` | | C-home | `x1b[1;5H` |
| C-S-up | `x1b[1;6A` | | C-S-down | `x1b[1;6B` |
| C-S-right | `x1b[1;6C` | | C-S-left | `x1b[1;6D` |
| C-S-end | `x1b[1;6F` | | C-S-home | `x1b[1;6H` |
| C-M-up | `x1b[1;7A` | | C-M-down | `x1b[1;7B` |
| C-M-right | `x1b[1;7C` | | C-M-left | `x1b[1;7D` |
| C-M-end | `x1b[1;7F` | | C-M-home | `x1b[1;7H` |
| C-M-S-up | `x1b[1;8A` | | C-M-S-down | `x1b[1;8B` |
| C-M-S-right | `x1b[1;8C` | | C-M-S-left | `x1b[1;8D` |
| C-M-S-end | `x1b[1;8F` | | C-M-S-home | `x1b[1;8H` |
| M-insert | `x1b[2;3~` | | M-S-insert | `x1b[2;4~` |
| C-insert | `x1b[2;5~` | | C-S-insert | `x1b[2;6~` |
| C-M-insert | `x1b[2;7~` | | C-M-S-insert | `x1b[2;8~` |
| S-delete | `x1b[3;2~` | | M-delete | `x1b[3;3~` |
| M-S-delete | `x1b[3;4~` | | C-delete | `x1b[3;5~` |
| C-S-delete | `x1b[3;6~` | | C-M-delete | `x1b[3;7~` |
| C-M-S-delete | `x1b[3;8~` | | S-prior | `x1b[5;2~` |
| M-prior | `x1b[5;3~` | | M-S-prior | `x1b[5;4~` |
| C-prior | `x1b[5;5~` | | C-S-prior | `x1b[5;6~` |
| C-M-prior | `x1b[5;7~` | | C-M-S-prior | `x1b[5;8~` |
| S-next | `x1b[6;2~` | | M-next | `x1b[6;3~` |
| M-S-next | `x1b[6;4~` | | C-next | `x1b[6;5~` |
| C-S-next | `x1b[6;6~` | | C-M-next | `x1b[6;7~` |
| C-M-S-next | `x1b[6;8~` | | C-backspace | `x1b[127;5u` |
| C-M-return | `x1b[13;13u` | | S-return | `x1b[13;2u` |
| C-return | `x1b[13;5u` | | C-S-return | `x1b[13;6u` |
| C-M-tab | `x1b[9;13u` | | [S-tab | `x1b[9;2u` |
| [C-tab | `x1b[9;5u` | | [C-S-tab | `x1b[9;6u` |
| C-M-S-1 | `x1b[33;14u` | | C-S-1 | `x1b[33;6u` |
| C-M- | `x1b[34;14u"` | | C- | `x1b[34;6u"` |
| C-M-S-3 | `x1b[35;14u` | | C-S-3 | `x1b[35;6u` |
| C-M-S-4 | `x1b[36;14u` | | C-S-4 | `x1b[36;6u` |
| C-M-S-5 | `x1b[37;14u` | | C-S-5 | `x1b[37;6u` |
| C-M-S-7 | `x1b[38;14u` | | C-S-7 | `x1b[38;6u` |
| C-M-' | `x1b[39;13u` | | C-' | `x1b[39;5u` |
| C-M-S-9 | `x1b[40;14u` | | C-S-9 | `x1b[40;6u` |
| C-M-S-0 | `x1b[41;14u` | | C-S-0 | `x1b[41;6u` |
| C-M-S-8 | `x1b[42;14u` | | C-S-8 | `x1b[42;6u` |
| C-M-S-= | `x1b[43;14u` | | C-S-= | `x1b[43;6u` |
| C-M-, | `x1b[44;13u` | | C-, | `x1b[44;5u` |
| C-M-. | `x1b[46;13u` | | C-. | `x1b[46;5u` |
| C-M-/ | `x1b[47;13u` | | C-/ | `x1b[47;5u` |
| C-M-0 | `x1b[48;13u` | | C-0 | `x1b[48;5u` |
| C-M-1 | `x1b[49;13u` | | C-1 | `x1b[49;5u` |
| C-M-2 | `x1b[50;13u` | | C-2 | `x1b[50;5u` |
| C-M-3 | `x1b[51;13u` | | C-3 | `x1b[51;5u` |
| C-M-4 | `x1b[52;13u` | | C-4 | `x1b[52;5u` |
| C-M-5 | `x1b[53;13u` | | C-5 | `x1b[53;5u` |
| C-M-6 | `x1b[54;13u` | | C-6 | `x1b[54;5u` |
| C-M-7 | `x1b[55;13u` | | C-7 | `x1b[55;5u` |
| C-M-8 | `x1b[56;13u` | | C-8 | `x1b[56;5u` |
| C-M-9 | `x1b[57;13u` | | C-9 | `x1b[57;5u` |
| C-M-: | `x1b[58;14u` | | C-: | `x1b[58;6u` |
| C-M-; | `x1b[59;13u` | | C-; | `x1b[59;5u` |
| C-M-S-, | `x1b[60;14u` | | C-S-, | `x1b[60;6u` |
| C-M-= | `x1b[61;13u` | | C-= | `x1b[61;5u` |
| C-M-S-. | `x1b[62;14u` | | C-S-. | `x1b[62;6u` |
| C-M- | `x1b[92;13u` | | | |

## 8 Color Escape Codes

| **Name** | | **Hex Color Code** | **Foreground Escape Code** | **Background Escape Code** |
| ---- | ---- | ---- | ---- | ---- |
| Black | <span style="color:black">████</span> | `#000000` | `x1b[1;30m` | `x1b[1;40m` |
| Red | <span style="color:red">████</span> | `#cc0000` | `x1b[1;31m` | `x1b[1;41m` |
| Green | <span style="color:green">████</span> | `#4e9a06` | `x1b[1;32m` | `x1b[1;42m` |
| Yellow | <span style="color:yellow">████</span> | `#c4a000` | `x1b[1;33m` | `x1b[1;43m` |
| Blue | <span style="color:blue">████</span> | `#729fcf` | `x1b[1;34m` | `x1b[1;44m` |
| Magenta | <span style="color:magenta">████</span> | `#75507b` | `x1b[1;35m` | `x1b[1;45m` |
| Cyan | <span style="color:cyan">████</span> | `#06989a` | `x1b[1;36m` | `x1b[1;46m` |
| White | <span style="color:white">████</span> | `#d3d7cf` | `x1b[1;37m` | `x1b[1;47m` |
| Default | | | `x1b[1;39m` | `x1b[1;49m` |

## 256 Color Escape Codes

| | **Name** | | **Hex Color Code** | **Foreground Escape Code** | **Background Escape Code** |
| --- | --- | --- | --- | --- | --- |
| 0 | Black (SYSTEM) | <span style="color:black">████</span> | `#000000` | `x1b[38:5:0m` | `x1b[48:5:0m` |
| 1 | Maroon (SYSTEM) | <span style="color:maroon">████</span> | `#800000` | `x1b[38:5:1m` | `x1b[48:5:1m` |
| 2 | Green (SYSTEM) | <span style="color:green">████</span> | `#008000` | `x1b[38:5:2m` | `x1b[48:5:2m` |
| 3 | Olive (SYSTEM) | <span style="color:olive">████</span> | `#808000` | `x1b[38:5:3m` | `x1b[48:5:3m` |
| 4 | Navy (SYSTEM) | <span style="color:navy">████</span> | `#000080` | `x1b[38:5:4m` | `x1b[48:5:4m` |
| 5 | Purple (SYSTEM) | <span style="color:purple">████</span> | `#800080` | `x1b[38:5:5m` | `x1b[48:5:5m` |
| 6 | Teal (SYSTEM) | <span style="color:teal">████</span> | `#008080` | `x1b[38:5:6m` | `x1b[48:5:6m` |
| 7 | Silver (SYSTEM) | <span style="color:silver">████</span> | `#c0c0c0` | `x1b[38:5:7m` | `x1b[48:5:7m` |
| 8 | Grey (SYSTEM) | <span style="color:grey">████</span> | `#808080` | `x1b[38:5:8m` | `x1b[48:5:8m` |
| 9 | Red (SYSTEM) | <span style="color:red">████</span> | `#ff0000` | `x1b[38:5:9m` | `x1b[48:5:9m` |
| 10 | Lime (SYSTEM) | <span style="color:lime">████</span> | `#00ff00` | `x1b[38:5:10m` | `x1b[48:5:10m` |
| 11 | Yellow (SYSTEM) | <span style="color:yellow">████</span> | `#ffff00` | `x1b[38:5:11m` | `x1b[48:5:11m` |
| 12 | Blue (SYSTEM) | <span style="color:blue">████</span> | `#0000ff` | `x1b[38:5:12m` | `x1b[48:5:12m` |
| 13 | Fuchsia (SYSTEM) | <span style="color:fuchsia">████</span> | `#ff00ff` | `x1b[38:5:13m` | `x1b[48:5:13m` |
| 14 | Aqua (SYSTEM) | <span style="color:aqua">████</span> | `#00ffff` | `x1b[38:5:14m` | `x1b[48:5:14m` |
| 15 | White (SYSTEM) | <span style="color:white">████</span> | `#ffffff` | `x1b[38:5:15m` | `x1b[48:5:15m` |
| 16 | Grey0 | <span style="color:grey0">████</span> | `#000000` | `x1b[38:5:16m` | `x1b[48:5:16m` |
| 17 | NavyBlue | <span style="color:#00005f;">████</span> | `#00005f` | `x1b[38:5:17m` | `x1b[48:5:17m` |
| 18 | DarkBlue | <span style="color:darkblue">████</span> | `#000087` | `x1b[38:5:18m` | `x1b[48:5:18m` |
| 19 | Blue3 | <span style="color:#0000cd;">████</span> | `#0000cd` | `x1b[38:5:19m` | `x1b[48:5:19m` |
| 20 | Blue2 | <span style="color:#0000ee;">████</span> | `#0000ee` | `x1b[38:5:20m` | `x1b[48:5:20m` |
| 21 | Blue1 | <span style="color:blue">████</span> | `#0000ff` | `x1b[38:5:21m` | `x1b[48:5:21m` |
| 22 | DarkGreen | <span style="color:darkgreen">████</span> | `#005f00` | `x1b[38:5:22m` | `x1b[48:5:22m` |
| 23 | DeepSkyBlue4 | <span style="color:#005f5f;">████</span> | `#005f5f` | `x1b[38:5:23m` | `x1b[48:5:23m` |
| 24 | DeepSkyBlue4 | <span style="color:#005f87;">████</span> | `#005f87` | `x1b[38:5:24m` | `x1b[48:5:24m` |
| 25 | DeepSkyBlue4 | <span style="color:#005faf;">████</span> | `#005faf` | `x1b[38:5:25m` | `x1b[48:5:25m` |
| 26 | DodgerBlue3 | <span style="color:#005fd7;">████</span> | `#005fd7` | `x1b[38:5:26m` | `x1b[48:5:26m` |
| 27 | DodgerBlue2 | <span style="color:#005fff;">████</span> | `#005fff` | `x1b[38:5:27m` | `x1b[48:5:27m` |
| 28 | Green4 | <span style="color:#008700;">████</span> | `#008700` | `x1b[38:5:28m` | `x1b[48:5:28m` |
| 29 | SpringGreen4 | <span style="color:#00875f;">████</span> | `#00875f` | `x1b[38:5:29m` | `x1b[48:5:29m` |
| 30 | Turquoise4 | <span style="color:#008787;">████</span> | `#008787` | `x1b[38:5:30m` | `x1b[48:5:30m` |
| 31 | DeepSkyBlue3 | <span style="color:#0087af;">████</span> | `#0087af` | `x1b[38:5:31m` | `x1b[48:5:31m` |
| 32 | DeepSkyBlue3 | <span style="color:#0087d7;">████</span> | `#0087d7` | `x1b[38:5:32m` | `x1b[48:5:32m` |
| 33 | DodgerBlue1 | <span style="color:#0087ff;">████</span> | `#0087ff` | `x1b[38:5:33m` | `x1b[48:5:33m` |
| 34 | Green3 | <span style="color:#00af00;">████</span> | `#00af00` | `x1b[38:5:34m` | `x1b[48:5:34m` |
| 35 | SpringGreen3 | <span style="color:#00af5f;">████</span> | `#00af5f` | `x1b[38:5:35m` | `x1b[48:5:35m` |
| 36 | DarkCyan | <span style="color:#00af87;">████</span> | `#00af87` | `x1b[38:5:36m` | `x1b[48:5:36m` |
| 37 | LightSeaGreen | <span style="color:#00afaf;">████</span> | `#00afaf` | `x1b[38:5:37m` | `x1b[48:5:37m` |
| 38 | DeepSkyBlue2 | <span style="color:#00afd7;">████</span> | `#00afd7` | `x1b[38:5:38m` | `x1b[48:5:38m` |
| 39 | DeepSkyBlue1 | <span style="color:#00afff;">████</span> | `#00afff` | `x1b[38:5:39m` | `x1b[48:5:39m` |
| 40 | Green3 | <span style="color:#00d700;">████</span> | `#00d700` | `x1b[38:5:40m` | `x1b[48:5:40m` |
| 41 | SpringGreen3 | <span style="color:#00d75f;">████</span> | `#00d75f` | `x1b[38:5:41m` | `x1b[48:5:41m` |
| 42 | SpringGreen2 | <span style="color:#00d787;">████</span> | `#00d787` | `x1b[38:5:42m` | `x1b[48:5:42m` |
| 43 | Cyan3 | <span style="color:#00d7af;">████</span> | `#00d7af` | `x1b[38:5:43m` | `x1b[48:5:43m` |
| 44 | DarkTurquoise | <span style="color:#00d7d7;">████</span> | `#00d7d7` | `x1b[38:5:44m` | `x1b[48:5:44m` |
| 45 | Turquoise2 | <span style="color:#00d7ff;">████</span> | `#00d7ff` | `x1b[38:5:45m` | `x1b[48:5:45m` |
| 46 | Green1 | <span style="color:#00ff00;">████</span> | `#00ff00` | `x1b[38:5:46m` | `x1b[48:5:46m` |
| 47 | SpringGreen2 | <span style="color:#00ff5f;">████</span> | `#00ff5f` | `x1b[38:5:47m` | `x1b[48:5:47m` |
| 48 | SpringGreen1 | <span style="color:#00ff87;">████</span> | `#00ff87` | `x1b[38:5:48m` | `x1b[48:5:48m` |
| 49 | MediumSpringGreen | <span style="color:#00ffaf;">████</span> | `#00ffaf` | `x1b[38:5:49m` | `x1b[48:5:49m` |
| 50 | Cyan2 | <span style="color:#00ffd7;">████</span> | `#00ffd7` | `x1b[38:5:50m` | `x1b[48:5:50m` |
| 51 | Cyan1 | <span style="color:#00ffff;">████</span> | `#00ffff` | `x1b[38:5:51m` | `x1b[48:5:51m` |
| 52 | DarkRed | <span style="color:#5f0000;">████</span> | `#5f0000` | `x1b[38:5:52m` | `x1b[48:5:52m` |
| 53 | DeepPink4 | <span style="color:#5f005f;">████</span> | `#5f005f` | `x1b[38:5:53m` | `x1b[48:5:53m` |
| 54 | Purple4 | <span style="color:#5f0087;">████</span> | `#5f0087` | `x1b[38:5:54m` | `x1b[48:5:54m` |
| 55 | Purple4 | <span style="color:#5f00af;">████</span> | `#5f00af` | `x1b[38:5:55m` | `x1b[48:5:55m` |
| 56 | Purple3 | <span style="color:#5f00d7;">████</span> | `#5f00d7` | `x1b[38:5:56m` | `x1b[48:5:56m` |
| 57 | BlueViolet | <span style="color:#5f00ff;">████</span> | `#5f00ff` | `x1b[38:5:57m` | `x1b[48:5:57m` |
| 58 | Orange4 | <span style="color:#5f5f00;">████</span> | `#5f5f00` | `x1b[38:5:58m` | `x1b[48:5:58m` |
| 59 | Grey37 | <span style="color:#5f5f5f;">████</span> | `#5f5f5f` | `x1b[38:5:59m` | `x1b[48:5:59m` |
| 60 | MediumPurple4 | <span style="color:#5f5f87;">████</span> | `#5f5f87` | `x1b[38:5:60m` | `x1b[48:5:60m` |
| 61 | SlateBlue3 | <span style="color:#5f5faf;">████</span> | `#5f5faf` | `x1b[38:5:61m` | `x1b[48:5:61m` |
| 62 | SlateBlue3 | <span style="color:#5f5fd7;">████</span> | `#5f5fd7` | `x1b[38:5:62m` | `x1b[48:5:62m` |
| 63 | RoyalBlue1 | <span style="color:#5f5fff;">████</span> | `#5f5fff` | `x1b[38:5:63m` | `x1b[48:5:63m` |
| 64 | Chartreuse4 | <span style="color:#5f8700;">████</span> | `#5f8700` | `x1b[38:5:64m` | `x1b[48:5:64m` |
| 65 | DarkSeaGreen4 | <span style="color:#5f875f;">████</span> | `#5f875f` | `x1b[38:5:65m` | `x1b[48:5:65m` |
| 66 | PaleTurquoise4 | <span style="color:#5f8787;">████</span> | `#5f8787` | `x1b[38:5:66m` | `x1b[48:5:66m` |
| 67 | SteelBlue | <span style="color:#5f87af;">████</span> | `#5f87af` | `x1b[38:5:67m` | `x1b[48:5:67m` |
| 68 | SteelBlue3 | <span style="color:#5f87d7;">████</span> | `#5f87d7` | `x1b[38:5:68m` | `x1b[48:5:68m` |
| 69 | CornflowerBlue | <span style="color:#5f87ff;">████</span> | `#5f87ff` | `x1b[38:5:69m` | `x1b[48:5:69m` |
| 70 | Chartreuse3 | <span style="color:#5faf00;">████</span> | `#5faf00` | `x1b[38:5:70m` | `x1b[48:5:70m` |
| 71 | DarkSeaGreen4 | <span style="color:#5faf5f;">████</span> | `#5faf5f` | `x1b[38:5:71m` | `x1b[48:5:71m` |
| 72 | CadetBlue | <span style="color:#5faf87;">████</span> | `#5faf87` | `x1b[38:5:72m` | `x1b[48:5:72m` |
| 73 | CadetBlue | <span style="color:#5fafaf;">████</span> | `#5fafaf` | `x1b[38:5:73m` | `x1b[48:5:73m` |
| 74 | SkyBlue3 | <span style="color:#5fafd7;">████</span> | `#5fafd7` | `x1b[38:5:74m` | `x1b[48:5:74m` |
| 75 | SteelBlue1 | <span style="color:#5fafff;">████</span> | `#5fafff` | `x1b[38:5:75m` | `x1b[48:5:75m` |
| 76 | Chartreuse3 | <span style="color:#5fd700;">████</span> | `#5fd700` | `x1b[38:5:76m` | `x1b[48:5:76m` |
| 77 | PaleGreen3 | <span style="color:#5fd75f;">████</span> | `#5fd75f` | `x1b[38:5:77m` | `x1b[48:5:77m` |
| 78 | SeaGreen3 | <span style="color:#5fd787;">████</span> | `#5fd787` | `x1b[38:5:78m` | `x1b[48:5:78m` |
| 79 | Aquamarine3 | <span style="color:#5fd7af;">████</span> | `#5fd7af` | `x1b[38:5:79m` | `x1b[48:5:79m` |
| 80 | MediumTurquoise | <span style="color:#5fd7d7;">████</span> | `#5fd7d7` | `x1b[38:5:80m` | `x1b[48:5:80m` |
| 81 | SteelBlue1 | <span style="color:#5fd7ff;">████</span> | `#5fd7ff` | `x1b[38:5:81m` | `x1b[48:5:81m` |
| 82 | Chartreuse2 | <span style="color:#5fff00;">████</span> | `#5fff00` | `x1b[38:5:82m` | `x1b[48:5:82m` |
| 83 | SeaGreen2 | <span style="color:#5fff5f;">████</span> | `#5fff5f` | `x1b[38:5:83m` | `x1b[48:5:83m` |
| 84 | SeaGreen1 | <span style="color:#5fff87;">████</span> | `#5fff87` | `x1b[38:5:84m` | `x1b[48:5:84m` |
| 85 | SeaGreen1 | <span style="color:#5fffaf;">████</span> | `#5fffaf` | `x1b[38:5:85m` | `x1b[48:5:85m` |
| 86 | Aquamarine1 | <span style="color:#5fffd7;">████</span> | `#5fffd7` | `x1b[38:5:86m` | `x1b[48:5:86m` |
| 87 | DarkSlateGray2 | <span style="color:#5fffff;">████</span> | `#5fffff` | `x1b[38:5:87m` | `x1b[48:5:87m` |
| 88 | DarkRed | <span style="color:#870000;">████</span> | `#870000` | `x1b[38:5:88m` | `x1b[48:5:88m` |
| 89 | DeepPink4 | <span style="color:#87005f;">████</span> | `#87005f` | `x1b[38:5:89m` | `x1b[48:5:89m` |
| 90 | DarkMagenta | <span style="color:#870087;">████</span> | `#870087` | `x1b[38:5:90m` | `x1b[48:5:90m` |
| 91 | DarkMagenta | <span style="color:#8700af;">████</span> | `#8700af` | `x1b[38:5:91m` | `x1b[48:5:91m` |
| 92 | DarkViolet | <span style="color:#8700d7;">████</span> | `#8700d7` | `x1b[38:5:92m` | `x1b[48:5:92m` |
| 93 | Purple | <span style="color:#8700ff;">████</span> | `#8700ff` | `x1b[38:5:93m` | `x1b[48:5:93m` |
| 94 | Orange4 | <span style="color:#875f00;">████</span> | `#875f00` | `x1b[38:5:94m` | `x1b[48:5:94m` |
| 95 | LightPink4 | <span style="color:#875f5f;">████</span> | `#875f5f` | `x1b[38:5:95m` | `x1b[48:5:95m` |
| 96 | Plum4 | <span style="color:#875f87;">████</span> | `#875f87` | `x1b[38:5:96m` | `x1b[48:5:96m` |
| 97 | MediumPurple3 | <span style="color:#875faf;">████</span> | `#875faf` | `x1b[38:5:97m` | `x1b[48:5:97m` |
| 98 | MediumPurple3 | <span style="color:#875fd7;">████</span> | `#875fd7` | `x1b[38:5:98m` | `x1b[48:5:98m` |
| 99 | SlateBlue1 | <span style="color:#875fff;">████</span> | `#875fff` | `x1b[38:5:99m` | `x1b[48:5:99m` |
| 100 | Yellow4 | <span style="color:#878700;">████</span> | `#878700` | `x1b[38:5:100m` | `x1b[48:5:100m` |
| 101 | Wheat4 | <span style="color:#87875f;">████</span> | `#87875f` | `x1b[38:5:101m` | `x1b[48:5:101m` |
| 102 | Grey53 | <span style="color:#878787;">████</span> | `#878787` | `x1b[38:5:102m` | `x1b[48:5:102m` |
| 103 | LightSlateGrey | <span style="color:#8787af;">████</span> | `#8787af` | `x1b[38:5:103m` | `x1b[48:5:103m` |
| 104 | MediumPurple | <span style="color:#8787d7;">████</span> | `#8787d7` | `x1b[38:5:104m` | `x1b[48:5:104m` |
| 105 | LightSlateBlue | <span style="color:#8787ff;">████</span> | `#8787ff` | `x1b[38:5:105m` | `x1b[48:5:105m` |
| 106 | Yellow4 | <span style="color:#87af00;">████</span> | `#87af00` | `x1b[38:5:106m` | `x1b[48:5:106m` |
| 107 | DarkOliveGreen3 | <span style="color:#87af5f;">████</span> | `#87af5f` | `x1b[38:5:107m` | `x1b[48:5:107m` |
| 108 | DarkSeaGreen | <span style="color:#87af87;">████</span> | `#87af87` | `x1b[38:5:108m` | `x1b[48:5:108m` |
| 109 | LightSkyBlue3 | <span style="color:#87afaf;">████</span> | `#87afaf` | `x1b[38:5:109m` | `x1b[48:5:109m` |
| 110 | LightSkyBlue3 | <span style="color:#87afd7;">████</span> | `#87afd7` | `x1b[38:5:110m` | `x1b[48:5:110m` |
| 111 | SkyBlue2 | <span style="color:#87afff;">████</span> | `#87afff` | `x1b[38:5:111m` | `x1b[48:5:111m` |
| 112 | Chartreuse2 | <span style="color:#87d700;">████</span> | `#87d700` | `x1b[38:5:112m` | `x1b[48:5:112m` |
| 113 | DarkOliveGreen3 | <span style="color:#87d75f;">████</span> | `#87d75f` | `x1b[38:5:113m` | `x1b[48:5:113m` |
| 114 | PaleGreen3 | <span style="color:#87d787;">████</span> | `#87d787` | `x1b[38:5:114m` | `x1b[48:5:114m` |
| 115 | DarkSeaGreen3 | <span style="color:#87d7af;">████</span> | `#87d7af` | `x1b[38:5:115m` | `x1b[48:5:115m` |
| 116 | DarkSlateGray3 | <span style="color:#87d7d7;">████</span> | `#87d7d7` | `x1b[38:5:116m` | `x1b[48:5:116m` |
| 117 | SkyBlue1 | <span style="color:#87d7ff;">████</span> | `#87d7ff` | `x1b[38:5:117m` | `x1b[48:5:117m` |
| 118 | Chartreuse1 | <span style="color:#87ff00;">████</span> | `#87ff00` | `x1b[38:5:118m` | `x1b[48:5:118m` |
| 119 | LightGreen | <span style="color:#87ff5f;">████</span> | `#87ff5f` | `x1b[38:5:119m` | `x1b[48:5:119m` |
| 120 | LightGreen | <span style="color:#87ff87;">████</span> | `#87ff87` | `x1b[38:5:120m` | `x1b[48:5:120m` |
| 121 | PaleGreen1 | <span style="color:#87ffaf;">████</span> | `#87ffaf` | `x1b[38:5:121m` | `x1b[48:5:121m` |
| 122 | Aquamarine1 | <span style="color:#87ffd7;">████</span> | `#87ffd7` | `x1b[38:5:122m` | `x1b[48:5:122m` |
| 123 | DarkSlateGray1 | <span style="color:#87ffff;">████</span> | `#87ffff` | `x1b[38:5:123m` | `x1b[48:5:123m` |
| 124 | Red3 | <span style="color:#af0000;">████</span> | `#af0000` | `x1b[38:5:124m` | `x1b[48:5:124m` |
| 125 | DeepPink4 | <span style="color:#af005f;">████</span> | `#af005f` | `x1b[38:5:125m` | `x1b[48:5:125m` |
| 126 | MediumVioletRed | <span style="color:#af0087;">████</span> | `#af0087` | `x1b[38:5:126m` | `x1b[48:5:126m` |
| 127 | Magenta3 | <span style="color:#af00af;">████</span> | `#af00af` | `x1b[38:5:127m` | `x1b[48:5:127m` |
| 128 | DarkViolet | <span style="color:#af00d7;">████</span> | `#af00d7` | `x1b[38:5:128m` | `x1b[48:5:128m` |
| 129 | Purple | <span style="color:#af00ff;">████</span> | `#af00ff` | `x1b[38:5:129m` | `x1b[48:5:129m` |
| 130 | DarkOrange3 | <span style="color:#af5f00;">████</span> | `#af5f00` | `x1b[38:5:130m` | `x1b[48:5:130m` |
| 131 | IndianRed | <span style="color:#af5f5f;">████</span> | `#af5f5f` | `x1b[38:5:131m` | `x1b[48:5:131m` |
| 132 | HotPink3 | <span style="color:#af5f87;">████</span> | `#af5f87` | `x1b[38:5:132m` | `x1b[48:5:132m` |
| 133 | MediumOrchid3 | <span style="color:#af5faf;">████</span> | `#af5faf` | `x1b[38:5:133m` | `x1b[48:5:133m` |
| 134 | MediumOrchid | <span style="color:#af5fd7;">████</span> | `#af5fd7` | `x1b[38:5:134m` | `x1b[48:5:134m` |
| 135 | MediumPurple2 | <span style="color:#af5fff;">████</span> | `#af5fff` | `x1b[38:5:135m` | `x1b[48:5:135m` |
| 136 | DarkGoldenrod | <span style="color:#af8700;">████</span> | `#af8700` | `x1b[38:5:136m` | `x1b[48:5:136m` |
| 137 | LightSalmon3 | <span style="color:#af875f;">████</span> | `#af875f` | `x1b[38:5:137m` | `x1b[48:5:137m` |
| 138 | RosyBrown | <span style="color:#af8787;">████</span> | `#af8787` | `x1b[38:5:138m` | `x1b[48:5:138m` |
| 139 | Grey63 | <span style="color:#af87af;">████</span> | `#af87af` | `x1b[38:5:139m` | `x1b[48:5:139m` |
| 140 | MediumPurple2 | <span style="color:#af87d7;">████</span> | `#af87d7` | `x1b[38:5:140m` | `x1b[48:5:140m` |
| 141 | MediumPurple1 | <span style="color:#af87ff;">████</span> | `#af87ff` | `x1b[38:5:141m` | `x1b[48:5:141m` |
| 142 | Gold3 | <span style="color:#afaf00;">████</span> | `#afaf00` | `x1b[38:5:142m` | `x1b[48:5:142m` |
| 143 | DarkKhaki | <span style="color:#afaf5f;">████</span> | `#afaf5f` | `x1b[38:5:143m` | `x1b[48:5:143m` |
| 144 | NavajoWhite3 | <span style="color:#afaf87;">████</span> | `#afaf87` | `x1b[38:5:144m` | `x1b[48:5:144m` |
| 145 | Grey69 | <span style="color:#afafaf;">████</span> | `#afafaf` | `x1b[38:5:145m` | `x1b[48:5:145m` |
| 146 | LightSteelBlue3 | <span style="color:#afafd7;">████</span> | `#afafd7` | `x1b[38:5:146m` | `x1b[48:5:146m` |
| 147 | LightSteelBlue | <span style="color:#afafff;">████</span> | `#afafff` | `x1b[38:5:147m` | `x1b[48:5:147m` |
| 148 | Yellow3 | <span style="color:#afd700;">████</span> | `#afd700` | `x1b[38:5:148m` | `x1b[48:5:148m` |
| 149 | DarkOliveGreen3 | <span style="color:#afd75f;">████</span> | `#afd75f` | `x1b[38:5:149m` | `x1b[48:5:149m` |
| 150 | DarkSeaGreen3 | <span style="color:#afd787;">████</span> | `#afd787` | `x1b[38:5:150m` | `x1b[48:5:150m` |
| 151 | DarkSeaGreen2 | <span style="color:#afd7af;">████</span> | `#afd7af` | `x1b[38:5:151m` | `x1b[48:5:151m` |
| 152 | LightCyan3 | <span style="color:#afd7d7;">████</span> | `#afd7d7` | `x1b[38:5:152m` | `x1b[48:5:152m` |
| 153 | LightSkyBlue1 | <span style="color:#afd7ff;">████</span> | `#afd7ff` | `x1b[38:5:153m` | `x1b[48:5:153m` |
| 154 | GreenYellow | <span style="color:#afff00;">████</span> | `#afff00` | `x1b[38:5:154m` | `x1b[48:5:154m` |
| 155 | DarkOliveGreen2 | <span style="color:#afff5f;">████</span> | `#afff5f` | `x1b[38:5:155m` | `x1b[48:5:155m` |
| 156 | PaleGreen1 | <span style="color:#afff87;">████</span> | `#afff87` | `x1b[38:5:156m` | `x1b[48:5:156m` |
| 157 | DarkSeaGreen2 | <span style="color:#afffaf;">████</span> | `#afffaf` | `x1b[38:5:157m` | `x1b[48:5:157m` |
| 158 | DarkSeaGreen1 | <span style="color:#afffd7;">████</span> | `#afffd7` | `x1b[38:5:158m` | `x1b[48:5:158m` |
| 159 | PaleTurquoise1 | <span style="color:#afffff;">████</span> | `#afffff` | `x1b[38:5:159m` | `x1b[48:5:159m` |
| 160 | Red3 | <span style="color:#d70000;">████</span> | `#d70000` | `x1b[38:5:160m` | `x1b[48:5:160m` |
| 161 | DeepPink3 | <span style="color:#d7005f;">████</span> | `#d7005f` | `x1b[38:5:161m` | `x1b[48:5:161m` |
| 162 | DeepPink3 | <span style="color:#d70087;">████</span> | `#d70087` | `x1b[38:5:162m` | `x1b[48:5:162m` |
| 163 | Magenta3 | <span style="color:#d700af;">████</span> | `#d700af` | `x1b[38:5:163m` | `x1b[48:5:163m` |
| 164 | Magenta3 | <span style="color:#d700d7;">████</span> | `#d700d7` | `x1b[38:5:164m` | `x1b[48:5:164m` |
| 165 | Magenta2 | <span style="color:#d700ff;">████</span> | `#d700ff` | `x1b[38:5:165m` | `x1b[48:5:165m` |
| 166 | DarkOrange3 | <span style="color:#d75f00;">████</span> | `#d75f00` | `x1b[38:5:166m` | `x1b[48:5:166m` |
| 167 | IndianRed | <span style="color:#d75f5f;">████</span> | `#d75f5f` | `x1b[38:5:167m` | `x1b[48:5:167m` |
| 168 | HotPink3 | <span style="color:#d75f87;">████</span> | `#d75f87` | `x1b[38:5:168m` | `x1b[48:5:168m` |
| 169 | HotPink2 | <span style="color:#d75faf;">████</span> | `#d75faf` | `x1b[38:5:169m` | `x1b[48:5:169m` |
| 170 | Orchid | <span style="color:#d75fd7;">████</span> | `#d75fd7` | `x1b[38:5:170m` | `x1b[48:5:170m` |
| 171 | MediumOrchid1 | <span style="color:#d75fff;">████</span> | `#d75fff` | `x1b[38:5:171m` | `x1b[48:5:171m` |
| 172 | Orange3 | <span style="color:#d78700;">████</span> | `#d78700` | `x1b[38:5:172m` | `x1b[48:5:172m` |
| 173 | LightSalmon3 | <span style="color:#d7875f;">████</span> | `#d7875f` | `x1b[38:5:173m` | `x1b[48:5:173m` |
| 174 | LightPink3 | <span style="color:#d78787;">████</span> | `#d78787` | `x1b[38:5:174m` | `x1b[48:5:174m` |
| 175 | Pink3 | <span style="color:#d787af;">████</span> | `#d787af` | `x1b[38:5:175m` | `x1b[48:5:175m` |
| 176 | Plum3 | <span style="color:#d787d7;">████</span> | `#d787d7` | `x1b[38:5:176m` | `x1b[48:5:176m` |
| 177 | Violet | <span style="color:#d787ff;">████</span> | `#d787ff` | `x1b[38:5:177m` | `x1b[48:5:177m` |
| 178 | Gold3 | <span style="color:#d7af00;">████</span> | `#d7af00` | `x1b[38:5:178m` | `x1b[48:5:178m` |
| 179 | LightGoldenrod3 | <span style="color:#d7af5f;">████</span> | `#d7af5f` | `x1b[38:5:179m` | `x1b[48:5:179m` |
| 180 | Tan | <span style="color:#d7af87;">████</span> | `#d7af87` | `x1b[38:5:180m` | `x1b[48:5:180m` |
| 181 | MistyRose3 | <span style="color:#d7afaf;">████</span> | `#d7afaf` | `x1b[38:5:181m` | `x1b[48:5:181m` |
| 182 | Thistle3 | <span style="color:#d7afd7;">████</span> | `#d7afd7` | `x1b[38:5:182m` | `x1b[48:5:182m` |
| 183 | Plum2 | <span style="color:#d7afff;">████</span> | `#d7afff` | `x1b[38:5:183m` | `x1b[48:5:183m` |
| 184 | Yellow3 | <span style="color:#d7d700;">████</span> | `#d7d700` | `x1b[38:5:184m` | `x1b[48:5:184m` |
| 185 | Khaki3 | <span style="color:#d7d75f;">████</span> | `#d7d75f` | `x1b[38:5:185m` | `x1b[48:5:185m` |
| 186 | LightGoldenrod2 | <span style="color:#d7d787;">████</span> | `#d7d787` | `x1b[38:5:186m` | `x1b[48:5:186m` |
| 187 | LightYellow3 | <span style="color:#d7d7af;">████</span> | `#d7d7af` | `x1b[38:5:187m` | `x1b[48:5:187m` |
| 188 | Grey84 | <span style="color:#d7d7d7;">████</span> | `#d7d7d7` | `x1b[38:5:188m` | `x1b[48:5:188m` |
| 189 | LightSteelBlue1 | <span style="color:#d7d7ff;">████</span> | `#d7d7ff` | `x1b[38:5:189m` | `x1b[48:5:189m` |
| 190 | Yellow2 | <span style="color:#d7ff00;">████</span> | `#d7ff00` | `x1b[38:5:190m` | `x1b[48:5:190m` |
| 191 | DarkOliveGreen1 | <span style="color:#d7ff5f;">████</span> | `#d7ff5f` | `x1b[38:5:191m` | `x1b[48:5:191m` |
| 192 | DarkOliveGreen1 | <span style="color:#d7ff87;">████</span> | `#d7ff87` | `x1b[38:5:192m` | `x1b[48:5:192m` |
| 193 | DarkSeaGreen1 | <span style="color:#d7ffaf;">████</span> | `#d7ffaf` | `x1b[38:5:193m` | `x1b[48:5:193m` |
| 194 | Honeydew2 | <span style="color:#d7ffd7;">████</span> | `#d7ffd7` | `x1b[38:5:194m` | `x1b[48:5:194m` |
| 195 | LightCyan1 | <span style="color:#d7ffff;">████</span> | `#d7ffff` | `x1b[38:5:195m` | `x1b[48:5:195m` |
| 196 | Red1 | <span style="color:#ff0000;">████</span> | `#ff0000` | `x1b[38:5:196m` | `x1b[48:5:196m` |
| 197 | DeepPink2 | <span style="color:#ff005f;">████</span> | `#ff005f` | `x1b[38:5:197m` | `x1b[48:5:197m` |
| 198 | DeepPink1 | <span style="color:#ff0087;">████</span> | `#ff0087` | `x1b[38:5:198m` | `x1b[48:5:198m` |
| 199 | DeepPink1 | <span style="color:#ff00af;">████</span> | `#ff00af` | `x1b[38:5:199m` | `x1b[48:5:199m` |
| 200 | Magenta2 | <span style="color:#ff00d7;">████</span> | `#ff00d7` | `x1b[38:5:200m` | `x1b[48:5:200m` |
| 201 | Magenta1 | <span style="color:#ff00ff;">████</span> | `#ff00ff` | `x1b[38:5:201m` | `x1b[48:5:201m` |
| 202 | OrangeRed1 | <span style="color:#ff5f00;">████</span> | `#ff5f00` | `x1b[38:5:202m` | `x1b[48:5:202m` |
| 203 | IndianRed1 | <span style="color:#ff5f5f;">████</span> | `#ff5f5f` | `x1b[38:5:203m` | `x1b[48:5:203m` |
| 204 | IndianRed1 | <span style="color:#ff5f87;">████</span> | `#ff5f87` | `x1b[38:5:204m` | `x1b[48:5:204m` |
| 205 | HotPink | <span style="color:#ff5faf;">████</span> | `#ff5faf` | `x1b[38:5:205m` | `x1b[48:5:205m` |
| 206 | HotPink | <span style="color:#ff5fd7;">████</span> | `#ff5fd7` | `x1b[38:5:206m` | `x1b[48:5:206m` |
| 207 | MediumOrchid1 | <span style="color:#ff5fff;">████</span> | `#ff5fff` | `x1b[38:5:207m` | `x1b[48:5:207m` |
| 208 | DarkOrange | <span style="color:#ff8700;">████</span> | `#ff8700` | `x1b[38:5:208m` | `x1b[48:5:208m` |
| 209 | Salmon1 | <span style="color:#ff875f;">████</span> | `#ff875f` | `x1b[38:5:209m` | `x1b[48:5:209m` |
| 210 | LightCoral | <span style="color:#ff8787;">████</span> | `#ff8787` | `x1b[38:5:210m` | `x1b[48:5:210m` |
| 211 | PaleVioletRed1 | <span style="color:#ff87af;">████</span> | `#ff87af` | `x1b[38:5:211m` | `x1b[48:5:211m` |
| 212 | Orchid2 | <span style="color:#ff87d7;">████</span> | `#ff87d7` | `x1b[38:5:212m` | `x1b[48:5:212m` |
| 213 | Orchid1 | <span style="color:#ff87ff;">████</span> | `#ff87ff` | `x1b[38:5:213m` | `x1b[48:5:213m` |
| 214 | Orange1 | <span style="color:#ffaf00;">████</span> | `#ffaf00` | `x1b[38:5:214m` | `x1b[48:5:214m` |
| 215 | SandyBrown | <span style="color:#ffaf5f;">████</span> | `#ffaf5f` | `x1b[38:5:215m` | `x1b[48:5:215m` |
| 216 | LightSalmon1 | <span style="color:#ffaf87;">████</span> | `#ffaf87` | `x1b[38:5:216m` | `x1b[48:5:216m` |
| 217 | LightPink1 | <span style="color:#ffafaf;">████</span> | `#ffafaf` | `x1b[38:5:217m` | `x1b[48:5:217m` |
| 218 | Pink1 | <span style="color:#ffafd7;">████</span> | `#ffafd7` | `x1b[38:5:218m` | `x1b[48:5:218m` |
| 219 | Plum1 | <span style="color:#ffafff;">████</span> | `#ffafff` | `x1b[38:5:219m` | `x1b[48:5:219m` |
| 220 | Gold1 | <span style="color:#ffd700;">████</span> | `#ffd700` | `x1b[38:5:220m` | `x1b[48:5:220m` |
| 221 | LightGoldenrod2 | <span style="color:#ffd75f;">████</span> | `#ffd75f` | `x1b[38:5:221m` | `x1b[48:5:221m` |
| 222 | LightGoldenrod2 | <span style="color:#ffd787;">████</span> | `#ffd787` | `x1b[38:5:222m` | `x1b[48:5:222m` |
| 223 | NavajoWhite1 | <span style="color:#ffd7af;">████</span> | `#ffd7af` | `x1b[38:5:223m` | `x1b[48:5:223m` |
| 224 | MistyRose1 | <span style="color:#ffd7d7;">████</span> | `#ffd7d7` | `x1b[38:5:224m` | `x1b[48:5:224m` |
| 225 | Thistle1 | <span style="color:#ffd7ff;">████</span> | `#ffd7ff` | `x1b[38:5:225m` | `x1b[48:5:225m` |
| 226 | Yellow1 | <span style="color:#ffff00;">████</span> | `#ffff00` | `x1b[38:5:226m` | `x1b[48:5:226m` |
| 227 | LightGoldenrod1 | <span style="color:#ffff5f;">████</span> | `#ffff5f` | `x1b[38:5:227m` | `x1b[48:5:227m` |
| 228 | Khaki1 | <span style="color:#ffff87;">████</span> | `#ffff87` | `x1b[38:5:228m` | `x1b[48:5:228m` |
| 229 | Wheat1 | <span style="color:#ffffaf;">████</span> | `#ffffaf` | `x1b[38:5:229m` | `x1b[48:5:229m` |
| 230 | Cornsilk1 | <span style="color:#ffffd7;">████</span> | `#ffffd7` | `x1b[38:5:230m` | `x1b[48:5:230m` |
| 231 | Grey100 | <span style="color:#ffffff;">████</span> | `#ffffff` | `x1b[38:5:231m` | `x1b[48:5:231m` |
| 232 | Grey3 | <span style="color:#080808;">████</span> | `#080808` | `x1b[38:5:232m` | `x1b[48:5:232m` |
| 233 | Grey7 | <span style="color:#121212;">████</span> | `#121212` | `x1b[38:5:233m` | `x1b[48:5:233m` |
| 234 | Grey11 | <span style="color:#1c1c1c;">████</span> | `#1c1c1c` | `x1b[38:5:234m` | `x1b[48:5:234m` |
| 235 | Grey15 | <span style="color:#262626;">████</span> | `#262626` | `x1b[38:5:235m` | `x1b[48:5:235m` |
| 236 | Grey19 | <span style="color:#303030;">████</span> | `#303030` | `x1b[38:5:236m` | `x1b[48:5:236m` |
| 237 | Grey23 | <span style="color:#3a3a3a;">████</span> | `#3a3a3a` | `x1b[38:5:237m` | `x1b[48:5:237m` |
| 238 | Grey27 | <span style="color:#444444;">████</span> | `#444444` | `x1b[38:5:238m` | `x1b[48:5:238m` |
| 239 | Grey30 | <span style="color:#4e4e4e;">████</span> | `#4e4e4e` | `x1b[38:5:239m` | `x1b[48:5:239m` |
| 240 | Grey35 | <span style="color:#585858;">████</span> | `#585858` | `x1b[38:5:240m` | `x1b[48:5:240m` |
| 241 | Grey39 | <span style="color:#626262;">████</span> | `#626262` | `x1b[38:5:241m` | `x1b[48:5:241m` |
| 242 | Grey42 | <span style="color:#6c6c6c;">████</span> | `#6c6c6c` | `x1b[38:5:242m` | `x1b[48:5:242m` |
| 243 | Grey46 | <span style="color:#767676;">████</span> | `#767676` | `x1b[38:5:243m` | `x1b[48:5:243m` |
| 244 | Grey50 | <span style="color:#808080;">████</span> | `#808080` | `x1b[38:5:244m` | `x1b[48:5:244m` |
| 245 | Grey54 | <span style="color:#8a8a8a;">████</span> | `#8a8a8a` | `x1b[38:5:245m` | `x1b[48:5:245m` |
| 246 | Grey58 | <span style="color:#949494;">████</span> | `#949494` | `x1b[38:5:246m` | `x1b[48:5:246m` |
| 247 | Grey62 | <span style="color:#9e9e9e;">████</span> | `#9e9e9e` | `x1b[38:5:247m` | `x1b[48:5:247m` |
| 248 | Grey66 | <span style="color:#a8a8a8;">████</span> | `#a8a8a8` | `x1b[38:5:248m` | `x1b[48:5:248m` |
| 249 | Grey70 | <span style="color:#b2b2b2;">████</span> | `#b2b2b2` | `x1b[38:5:249m` | `x1b[48:5:249m` |
| 250 | Grey74 | <span style="color:#bcbcbc;">████</span> | `#bcbcbc` | `x1b[38:5:250m` | `x1b[48:5:250m` |
| 251 | Grey78 | <span style="color:#c6c6c6;">████</span> | `#c6c6c6` | `x1b[38:5:251m` | `x1b[48:5:251m` |
| 252 | Grey82 | <span style="color:#d0d0d0;">████</span> | `#d0d0d0` | `x1b[38:5:252m` | `x1b[48:5:252m` |
| 253 | Grey85 | <span style="color:#dadada;">████</span> | `#dadada` | `x1b[38:5:253m` | `x1b[48:5:253m` |
| 254 | Grey89 | <span style="color:#e4e4e4;">████</span> | `#e4e4e4` | `x1b[38:5:254m` | `x1b[48:5:254m` |
| 255 | Grey93 | <span style="color:#eeeeee;">████</span> | `#eeeeee` | `x1b[38:5:255m` | `x1b[48:5:255m` |

## True Color

| | **Escape Code** | **Example** |
| --- | --- | --- |
| foreground color | `x1b[38;2;${red};${green};${blue}m` | `x1b[38;2;255;0;0m` |
| background color | `x1b[48;2;${red};${green};${blue}m` | `x1b[48;2;255;0;0m` |

## See also

- [Screen](screen.md)
- [Tmux](tmux.md)
- [iTerm2](iterm2.md)
- [Shortcuts](../keyboard/shortcuts.md)
- [xmodmap](../keyboard/xmodmap.md)
- [xvkbd](../keyboard/xvkbd.md)
- [xbindkeys](../keyboard/xbindkeys.md)
- [Kitty](kitty/kitty.md)

## Resources

- [Wikipedia: ANSI escape code](https://en.wikipedia.org/wiki/ANSI_escape_code)
- [Wikipedia: X11 color names](https://en.wikipedia.org/wiki/X11_color_names)
- [Build your own Command Line with ANSI escape codes](http://www.lihaoyi.com/post/BuildyourownCommandLinewithANSIescapecodes.html)
- [ANSI Escape Sequences gist](https://gist.github.com/fnky/458719343aabd01cfb17a3a4f7296797)
- [ascii-table: ANSI Escape sequences](http://ascii-table.com/ansi-escape-sequences.php)
- [bluesock: ansi codes](https://bluesock.org/~willkg/dev/ansi.html)
- [bash-hackers: Terminal Codes (ANSI/VT100) introduction](http://wiki.bash-hackers.org/scripting/terminalcodes)
- [XTerm Control Sequences](https://invisible-island.net/xterm/ctlseqs/ctlseqs.html)
- [XTerm RGB color chart](http://www.calmar.ws/vim/256-xterm-24bit-rgb-color-chart.html)
- [VT100 – Various terminal manuals](https://vt100.net/)
- [xterm.js – Supported Terminal Sequences](https://xtermjs.org/docs/api/vtfeatures/)
