# xvkbd tutorial

`xvkbd` is command line tool that lets you send a keyboard key signal or mouse click.

`xvkbd` is a virtual (graphical) keyboard program for X Window System which provides a facility to enter characters onto other clients (software) by clicking on a keyboard displayed on the screen. This may be used for systems without a hardware keyboard such as kiosk terminals or handheld devices. This program also has a facility to send characters specified as the command line option to another client.

## Install xvkbd
```shell
sudo apt-get install xvkbd
```

## xvkbd Command Example

### Send the key control+c

```shell
xvkbd -no-jump-pointer -xsendevent -text '\Cc'
```

### Send mouse left click

```shell
xvkbd -no-jump-pointer -xsendevent -text '\m1'
```

## xvkbd Key syntax

| **Key** | **Description** |
| --- | --- |
| `\[F1]` | F1 |
| `\[F2]` | F2 |
| `\[Print]` | PrintScreen (Print Screen) |
| `\[Scroll_Lock]` | ScrollLock (Scroll Lock) |
| `\[Pause/Break]` | Pause (Pause/Break) |
| `\r` | Return |
| `\t` | Tab |
| `\e` | Escape (escape) |
| `\b` | Backspace |
| `\d` | Delete |
| `\S` | Shift (modify the next character) |
| `\C` | Ctrl (modify the next character) |
| `\A` | Alt (modify the next character) |
| `\M` | Meta (modify the next character) |
| `\[keysym]` | keysym is X11's key syntax. (For example, \[Left]) |
| `\m1` | Mouse left click |
| `\m2` | Mouse middle click |
| `\m3` | Mouse right click |
| `\mdigit` | Mouse click of the specified mouse button. |

## Bind Keys to Command
For xvkbd to be useful, you need to bind keys to command.

For example, make F2 do Ctrl+c.

## See also

- [xbindkeys](xbindkeys.md)
- [xmodmap](xmodmap.md)
- [iTerm2](../terminal/iterm2.md)
- [Screen](../terminal/screen.md)
- [Shortcuts](shortcuts.md)
- [Tmux](../terminal/tmux.md)
- [Kitty](../terminal/kitty/kitty.md)
