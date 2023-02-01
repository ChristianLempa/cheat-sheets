# xbindkeys tutorial

`xbindkeys` is a tool to let you create keyboard shortcuts to run shell commands, globally.

`xbindkeys` allows you to launch shell commands with your keyboard or your mouse under X Window. It links commands to keys or mouse buttons, using a configuration file. It's independant of the window manager and can capture all keyboard keys

`xbindkeys` can bind almost any key or key combination. Example: `CapsLock`, `ScrLk`, `Pause`, `F2`, number pad keys, multimedia keys, and special app launch buttons, and also standard modifier key combinations such as `Menu`, `Ctrl+3`, `Super+3`, etc.

## Install xbindkeys

```shell
sudo apt-get install xbindkeys
```

## xbindkeys config file

Create a file at

`~/.xbindkeysrc`

Add the following content:

```text
# sample xbindkeys config
# place this file at ~/.xbindkeysrc

# make F8 launch Google Chrome browser
"google-chrome"
F8

# make F3 do Ctrl+c
"xvkbd -no-jump-pointer -xsendevent -text '\Cc'"
F3
```

Mouse button example:

```text
# mouse button 9 sends Control + PageUp
"xvkbd -xsendevent -text '\C\[Page_Up]'"
b:9

# mouse button 8 sends Control + PageDown
"xvkbd -xsendevent -text '\C\[Page_Down]'"
b:8
```

For each keybinding in this example, the xbindkeys config takes 2 lines.

- the first line is a shell command.
- the second line is the key to bind to.

## Reload the Config File

```shell
# make xbindkeys reload config
killall -s1 xbindkeys
```

Start xbindkeys:

```shell
# start xbindkeys daemon
xbindkeys -f ~/.xbindkeysrc
```

## Actions

To fully use `xbindkeys`, you need to know what shell scripts to call.

### Sending Keys

To have shell command send keys, you need to install [xvkbd](xvkbd.md).

### Launching App

Use the app's command name directly. For example,

- firefox
- google-chrome
- gnome-terminal
- nautilus

### Open File

Call `xdg-open` to open file.

```shell
xdg-open ~/todo.txt
```

## See also

- [xmodmap](xmodmap.md)
- [xvkbd](xvkbd.md)
- [iTerm2](../terminal/iterm2.md)
- [Screen](../terminal/screen.md)
- [Shortcuts](shortcuts.md)
- [Tmux](../terminal/tmux.md)
- [Kitty](../terminal/kitty/kitty.md)
