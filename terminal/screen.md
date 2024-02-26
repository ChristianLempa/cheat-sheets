---
tags:
    - terminal
    - session
    - utility
categories:
    - terminal
---

# Screen

GNU Screen is a terminal multiplexer, a software application that can be used to multiplex several virtual consoles, allowing a user to access multiple separate login sessions inside a single terminal window, or detach and reattach sessions from a terminal. It is useful for dealing with multiple programs from a command line interface, and for separating programs from the session of the Unix shell that started the program, particularly so a remote process continues running even when the user is disconnected.

Released under the terms of version 3 or later of the GNU General Public License, GNU Screen is free software.

This is a quick reference guide cheat sheet for the screen command.

## Getting started

```bash
screen 
```
1\. Press <kbd>Ctrl-A</kbd> <kbd>D</kbd> to detach session

---

2\. List all screen sessions
```bash
screen -ls
```
3\. Re-attach a screen Session
```bash
screen -r <name/pid>
```

## Options
| Options | Example                               | Description                                             |
|---------|---------------------------------------|---------------------------------------------------------|
| `-S`    | screen -S debug                       | Start a new session with session name                   |
| `-ls`   | screen -ls                            | List running sessions / screens                         |
| `-x`    | screen -x                             | Attach to a running session                             |
| `-r`    | screen -r debug                       | Attach to a running session with name                   |
| `-R`    | screen -R debug                       | Attach to a session _(Will create if it doesn't exist)_ |
| `-d`    | screen -d -m wget xxxx.com/large.file | Start screen in detached mode                           |
| `-X`    | screen -X -S debug kill               | Kill a running session                                  |

## Help

| Command      | Description                    |
|--------------|--------------------------------|
| `Ctrl-A` `?` | See help _(Lists keybindings)_ |

## Window Management
| Command                                | Description                             |
|----------------------------------------|-----------------------------------------|
| `Ctrl-A` `C`                           | Create new window                       |
| `Ctrl-A` `Ctrl-A`                      | Change to last-visited active window    |
| `Ctrl-A` `0...9`                       | Change to window by number              |
| `Ctrl-A` `'` `<0...9 or title>`        | Change to window by number or name      |
| `Ctrl-A` `N` or `Ctrl-A` `<space>`     | Change to next window in list           |
| `Ctrl-A` `P` or `Ctrl-A` `<backspace>` | Change to previous window in list       |
| `Ctrl-A` `"`                           | See window list                         |
| `Ctrl-A` `W`                           | Show window bar                         |
| `Ctrl-A` `K`                           | Kill current window _(not recommended)_ |
| `Ctrl-A` `\`                           | Kill all windows _(not recommended)_    |
| `Ctrl-A` `A`                           | Rename current window                   |

## Getting Out

| Command          | Description                               |
|------------------|-------------------------------------------|
| `Ctrl-A` `D`     | Detach                                    |
| `Ctrl-A` `D` `D` | Detach and logout <br>_(quick exit)_      |
| `Ctrl-A` `:`     | Exit all session                          |
| `Ctrl-A` `C-\`   | Force-exit screen <br>_(not recommended)_ |

## Split screen
| Command        | Description                            |
|----------------|----------------------------------------|
| `Ctrl-A` `S`   | Split display horizontally             |
| `Ctrl-A` `V`   | Split display vertically               |
| `Ctrl-A` `|`   | Split display vertically               |
| `Ctrl-A` `TAB` | Jump to next display region            |
| `Ctrl-A` `X`   | Remove current region                  |
| `Ctrl-A` `Q`   | Remove all regions but the current one |

## Misc

| Command           | Description                                |
|-------------------|--------------------------------------------|
| `Ctrl-A` `C-l`    | Redraw window                              |
| `Ctrl-A` `[`      | Copy mode                                  |
| `Ctrl-A` `ESC`    | Copy mode                                  |
| `Ctrl-A` `]`      | Paste                                      |
| `Ctrl-A` `M`      | Monitor window for activity                |
| `Ctrl-A` `_`      | Monitor window for silence                 |
| `Ctrl-A` `Ctrl-V` | Enter digraph <br>_(non-ASCII characters)_ |
| `Ctrl-A` `X`      | Lock (password protect) display            |
| `Ctrl-A` `:`      | Enter screen command                       |
| `Ctrl-A` `H`      | Enable logging in the screen session       |

## Screen tricks
SSH and attach in one line
```bash
ssh -t user@host screen -x <name/pid>
```

## See also

- [Escape Codes](escape_codes.md)
- [Tmux](tmux.md)
- [iTerm2](iterm2.md)
- [Shortcuts](../keyboard/shortcuts.md)
- [xmodmap](../keyboard/xmodmap.md)
- [xvkbd](../keyboard/xvkbd.md)
- [xbindkeys](../keyboard/xbindkeys.md)
- [Kitty](kitty/kitty.md)
