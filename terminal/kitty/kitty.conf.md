# Kitty example configuration

```
## Default Kitty configuration
#
## Window size and decoration
remember_window_size  no
initial_window_width  92c
initial_window_height 26c
hide_window_decorations no
confirm_os_window_close -1
#
## Colors
foreground #dddddd
background #000000
background_opacity 0.8
#
## Cursor
cursor_shape underline
cursor_underline_thickness 2.0
cursor_blink_interval -1
cursor_stop_blinking_after 15.0
#
## Font
font_family      monospace
bold_font        auto
italic_font      auto
bold_italic_font auto
font_size        28.0
#
## Clipboard
copy_on_select   yes
map ctrl+c       copy_or_interrupt
map kitty_mod+c  copy_to_clipboard
map cmd+c        copy_to_clipboard
map ctrl+v       paste_from_clipboard
map kitty_mod+v  paste_from_clipboard
map cmd+v        paste_from_clipboard
map kitty_mod+s  paste_from_selection
map shift+insert paste_from_selection
#
## Keyboard mappings
map F5 launch --location=hsplit
map F6 launch --location=vsplit
# Shift the currently in focus window
map shift+up move_window up
map shift+left move_window left
map shift+right move_window right
map shift+down move_window down
# Mac-specific since 'cmd'
map cmd+left neighboring_window left
map cmd+right neighboring_window right
map cmd+up neighboring_window up
map cmd+down neighboring_window down
# RESIZING WINDOWS
map option+left resize_window narrower
map option+right resize_window wider
map option+up resize_window taller
map option+down resize_window shorter 3
map kitty_mod+w close_window
map shift+cmd+d close_window
map shift+cmd+w close_os_window
# Select specific layouts
map ctrl+alt+f goto_layout fat
map ctrl+alt+t goto_layout tall
map ctrl+alt+s goto_layout stack
map ctrl+alt+h goto_layout horizontal
map ctrl+alt+v goto_layout vertical
#
## Custom startup session
#startup_session ./sessions/startup
#
## Layouts
#
# The enabled layouts and their order (first is default)
#
# Supported layouts (currently these seven)
#
# Fat -- One (or optionally more) windows are shown full width on the top,
#        the rest of the windows are shown side-by-side on the bottom
# Grid -- All windows are shown in a grid
# Horizontal -- All windows are shown side-by-side
# Splits -- Windows arranged in arbitrary patterns created using horizontal
#           and vertical splits
# Stack -- Only a single maximized window is shown at a time
# Tall -- One (or optionally more) windows are shown full height on the left,
#         the rest of the windows are shown one below the other on the right
# Vertical -- All windows are shown one below the other
#
enabled_layouts tall:bias=70,fat:bias=80,all
#
## Enhancements
allow_hyperlinks yes
shell_integration no-cursor
#
## Tabs
bell_on_tab "🔔 "
tab_bar_edge bottom
tab_bar_margin_width 0.0
#tab_bar_margin_height 0.0 0.0
tab_bar_margin_height 5.0 0.0
#tab_bar_style fade
tab_bar_style custom
#tab_fade 0.25 0.5 0.75 1
tab_fade 0 0 0 0
tab_bar_align left
tab_bar_min_tabs 1
tab_switch_strategy previous
#tab_separator " ┇"
tab_separator ""
tab_powerline_style angled
tab_activity_symbol none
tab_title_template "{fmt.fg._415c6d}{fmt.bg.default}  {f'{title[:6]}…{title[-8:]}' if title.rindex(title[-1]) + 1 > 25 else ('Home' if title.rindex(title[-1]) + 1 < 2 else title)}{' []' if layout_name == 'stack' else ''} "
active_tab_title_template "{fmt.fg._83b6af}{fmt.bg.default}  {f'{title[:10]}…{title[-12:]}' if title.rindex(title[-1]) + 1 > 25 else ('Home' if title.rindex(title[-1]) + 1 < 2 else title)}{' []' if layout_name == 'stack' else ''} "
active_tab_foreground   #000
active_tab_background   #eee
active_tab_font_style   bold
inactive_tab_foreground #444
inactive_tab_background #999
inactive_tab_font_style normal
#tab_bar_background     #003747
tab_bar_background      none
tab_bar_margin_color    none
map kitty_mod+right     next_tab
map shift+cmd+]         next_tab
map ctrl+tab            next_tab
map kitty_mod+left      previous_tab
map shift+cmd+[         previous_tab
map ctrl+shift+tab      previous_tab
map kitty_mod+t         new_tab
map cmd+t               new_tab
map kitty_mod+q         close_tab
map cmd+w               close_tab
map kitty_mod+.         move_tab_forward
map kitty_mod+,         move_tab_backward
map kitty_mod+alt+t     set_tab_title
map shift+cmd+i         set_tab_title
#
## Theme
#include themes/megaforest.conf
#include themes/Floraverse.conf
#include themes/Tango_Dark.conf
#include themes/LiquidCarbonTransparent.conf
#include themes/Solarized_Dark_Higher_Contrast.conf
#include themes/Asciiville.conf
#
## URL Handling
#
url_prefixes file ftp ftps gemini git gopher http https irc ircs kitty mailto news sftp ssh
#: The color and style for highlighting URLs on mouse-over. url_style
#: can be one of: none, straight, double, curly, dotted, dashed.
url_color                   #0087bd
url_style                   curly
#open_url_with              default
#open_url_with              firefox
#open_url_with              w3m
open_url_with               __SET__BROWSER__
detect_urls                 yes
paste_actions               quote-urls-at-prompt
map kitty_mod+e             open_url_with_hints
map shift+cmd+k             open_url https://sw.kovidgoyal.net/kitty/
map shift+cmd+m             open_url https://github.com/doctorfree/MusicPlayerPlus#readme
map shift+cmd+a             open_url https://github.com/doctorfree/Asciiville#readme
#
## Advanced
#
# These features are only available in recent versions of Kitty
# Ubuntu 20.04 is still at kitty 0.15.0 which does not support these
# Asciiville installs kitty >= 0.25.2 which does support these
#
#globinclude kitty.d/**/*.conf
#envinclude KITTY_CONF_*
#
# Example kitty invocation to listen for control messages on a specified socket:
#   kitty -o allow_remote_control=yes --listen-on unix:/tmp/kitty
# Control this instance of kitty using command line arguments to kitty:
#   kitty @ --to unix:/tmp/kitty ls
#allow_remote_control socket-only
#listen_on unix:/tmp/kitty
```
## See also

- [Kitty](kitty.md)
- [Kitty tab bar](tab_bar.py.md)
