# Kitty

kitty is a free and open-source graphics processing unit (GPU) accelerated terminal emulator for Linux and macOS focused on performance and features. kitty is written in a mix of C and Python programming languages. It provides GPU support.

See https://sw.kovidgoyal.net/kitty/conf/

## Table of Contents

1. [Usage](#usage)
    1. [Override options](#override-options)
    1. [Command option](#command-option)
    1. [Single instance options](#single-instance-options)
1. [Window size](#window-size)
1. [Window decoration](#window-decoration)
1. [Color scheme](#color-scheme)
1. [Cursor](#cursor)
1. [Fonts](#fonts)
1. [Include directives](#include-directives)
1. [Auto copy selection](#auto-copy-selection)
1. [Kitty fonts](#kitty-fonts)
1. [See also](#see-also)

## Usage

**kitty** [options] [program-to-run ...]

### Override options

To override a configuration option, use `-o <option>`.

For example, to override the font size configuration:

```
kitty -o font_size=20
```

### Command option

Specify the command to run after all options on the command line:

```
kitty --hold sh -c "echo hello, world"
```

### Single instance options

```
--single-instance, -1
```

If specified only a single instance of kitty will run. New invocations will
instead create a new top-level window in the existing kitty instance. This
allows kitty to share a single sprite cache on the GPU and also reduces
startup time. You can also have separate groups of kitty instances by using
the `kitty --instance-group` option.

```
--instance-group <INSTANCE_GROUP>
```

Used in combination with the `kitty --single-instance` option. All kitty
invocations with the same kitty --instance-group will result in new windows
being created in the first kitty instance within that group.

```
--wait-for-single-instance-window-close
```

Normally, when using `kitty --single-instance`, kitty will open a new window
in an existing instance and quit immediately. With this option, it will not
quit till the newly opened window is closed. Note that if no previous instance
is found, then kitty will wait anyway, regardless of this option.

## Window size

```
remember_window_size  yes
initial_window_width  82c
initial_window_height 24c
```

## Window decoration

```
hide_window_decorations yes
```

## Color scheme

```
foreground #dddddd
background #000000
background_opacity 1.0
```

## Cursor

Can be block beam or underline

```
cursor_shape underline
```

## Fonts

```
font_family      monospace
bold_font        auto
italic_font      auto
bold_italic_font auto
font_size        11.0
```

## Include directives

```
include other.conf
# Include *.conf files from all subdirs of kitty.d inside the kitty config dir
globinclude kitty.d/**/*.conf
# Include the *contents* of all env vars starting with KITTY_CONF_
envinclude KITTY_CONF_*
```

## Auto copy selection

```
# This copies selected text to a private buffer named a1
# The keyboard shortcut shift+cmd+v pastes the contents of the a1 buffer
copy_on_select a1
map shift+cmd+v paste_from_buffer a1
```

## Kitty fonts

Output of `kitty +list-fonts` on Ubuntu 20.04

```
3270 Condensed
    3270 Condensed

3270 Semi-Condensed
    3270 Semi-Condensed

Andale Mono
    Andale Mono
    Andale Mono

Courier 10 Pitch
    Courier 10 Pitch Bold
    Courier 10 Pitch Bold Italic
    Courier 10 Pitch Italic
    Courier 10 Pitch Regular

Courier New
    Courier New
    Courier New
    Courier New Bold
    Courier New Bold
    Courier New Bold Italic
    Courier New Bold Italic
    Courier New Italic
    Courier New Italic

DejaVu Sans Mono
    DejaVu Sans Mono
    DejaVu Sans Mono Bold
    DejaVu Sans Mono Bold Oblique
    DejaVu Sans Mono Oblique

FreeMono
    FreeMono
    FreeMono Bold
    FreeMono Bold Oblique
    FreeMono Oblique

Hack
    Hack Bold
    Hack Bold Italic
    Hack Italic
    Hack Regular

ibm3270
    3270

Inconsolata
    Inconsolata

Liberation Mono
    Liberation Mono
    Liberation Mono Bold
    Liberation Mono Bold Italic
    Liberation Mono Italic

Mitra Mono
    Mitra Mono

mononoki Nerd Font Mono
    mononoki Bold Italic Nerd Font Complete Mono
    mononoki Bold Nerd Font Complete Mono
    mononoki Italic Nerd Font Complete Mono
    mononoki-Regular Nerd Font Complete Mono

Nimbus Mono L
    Nimbus Mono L Bold
    Nimbus Mono L Regular
    Nimbus Mono L Regular Oblique

Nimbus Mono PS
    Nimbus Mono PS Bold
    Nimbus Mono PS Bold Italic
    Nimbus Mono PS Italic
    Nimbus Mono PS Regular
    NimbusMonoPS-Bold
    NimbusMonoPS-BoldItalic
    NimbusMonoPS-Italic
    NimbusMonoPS-Regular

Noto Mono
    Noto Mono

Tlwg Mono
    Tlwg Mono
    Tlwg Mono Bold
    Tlwg Mono Bold Oblique
    Tlwg Mono Oblique

Tlwg Typo
    Tlwg Typo
    Tlwg Typo Bold
    Tlwg Typo Bold Oblique
    Tlwg Typo Oblique

Ubuntu Mono
    Ubuntu Mono
    Ubuntu Mono Bold
    Ubuntu Mono Bold Italic
    Ubuntu Mono Italic

Ubuntu Nerd Font Mono
    Ubuntu Bold Italic Nerd Font Complete Mono
    Ubuntu Bold Nerd Font Complete Mono
    Ubuntu Italic Nerd Font Complete Mono
    Ubuntu Light Italic Nerd Font Complete Mono
    Ubuntu Light Nerd Font Complete Mono
    Ubuntu Medium Italic Nerd Font Complete Mono
    Ubuntu Medium Nerd Font Complete Mono
    Ubuntu Nerd Font Complete Mono

UbuntuCondensed Nerd Font Mono
    Ubuntu Condensed Nerd Font Complete Mono

UbuntuMono Nerd Font Mono
    Ubuntu Mono Bold Italic Nerd Font Complete Mono
    Ubuntu Mono Bold Nerd Font Complete Mono
    Ubuntu Mono Italic Nerd Font Complete Mono
    Ubuntu Mono Nerd Font Complete Mono

VictorMono Nerd Font Mono
    Victor Mono Bold Italic Nerd Font Complete Mono
    Victor Mono Bold Nerd Font Complete Mono
    Victor Mono Bold Oblique Nerd Font Complete Mono
    Victor Mono ExtraLight Italic Nerd Font Complete Mono
    Victor Mono ExtraLight Nerd Font Complete Mono
    Victor Mono ExtraLight Oblique Nerd Font Complete Mono
    Victor Mono Italic Nerd Font Complete Mono
    Victor Mono Light Italic Nerd Font Complete Mono
    Victor Mono Light Nerd Font Complete Mono
    Victor Mono Light Oblique Nerd Font Complete Mono
    Victor Mono Medium Italic Nerd Font Complete Mono
    Victor Mono Medium Nerd Font Complete Mono
    Victor Mono Medium Oblique Nerd Font Complete Mono
    Victor Mono Oblique Nerd Font Complete Mono
    Victor Mono Regular Nerd Font Complete Mono
    Victor Mono SemiBold Italic Nerd Font Complete Mono
    Victor Mono SemiBold Nerd Font Complete Mono
    Victor Mono SemiBold Oblique Nerd Font Complete Mono
    Victor Mono Thin Italic Nerd Font Complete Mono
    Victor Mono Thin Nerd Font Complete Mono
    Victor Mono Thin Oblique Nerd Font Complete Mono
```

## See also

- [Kitty configuration](kitty.conf.md)
- [Kitty tab bar](tab_bar.py.md)
- [iTerm2](../iterm2.md)
- [Screen](../screen.md)
- [Tmux](../tmux.md)
