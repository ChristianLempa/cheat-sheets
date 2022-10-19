---
tags:
    - utility
    - terminal
    - session
categories:
    - terminal
---

# Tmux

Tmux is an open-source terminal multiplexer for Unix-like operating systems. It allows multiple terminal sessions to be accessed simultaneously in a single window. It is useful for running more than one command-line program at the same time. It can also be used to detach processes from their controlling terminals, allowing remote sessions to remain active without being visible.

Repository: https://github.com/tmux/tmux

Tmux Wiki: https://github.com/tmux/tmux/wiki (very helpful)

Website: https://tmux.github.io/

## Contents

1. [Installing](#installing)
1. [Cheat sheet](#cheat-sheet)
1. [Tmux shortcuts](#tmux-shortcuts)
1. [Tmux Command Mode](#tmux-command-mode)
1. [Example tmux session](#example-tmux-session)
1. [Example tmux configuration](#example-tmux-configuration)
1. [Custom key bindings](#custom-key-bindings)
1. [Window options](#window-options)
1. [General options](#general-options)
1. [See also](#see-also)

## Installing

See the [Installing](https://github.com/tmux/tmux/wiki/Installing) article
on the Tmux wiki for complete installation instructions including building
tmux from source.

### Binary packages

Many platforms provide prebuilt packages of tmux, although these are often out
of date. Details of the commands to discover and install these can be found in
the documentation for the platform package management tools, for example:

Platform|Install Command
---|---
Arch Linux|`pacman -S tmux`
Debian or Ubuntu|`apt install tmux`
Fedora|`dnf install tmux`
RHEL or CentOS|`yum install tmux`
macOS (using Homebrew|`brew install tmux`
macOS (using MacPorts)|`port install tmux`
openSUSE|`zypper install tmux`

### AppImage package

Instructions and scripts on building an AppImage package for tmux are available
[from Nelson Enzo here](https://github.com/nelsonenzo/tmux-appimage). Prebuilt
AppImage packages are also available
[here](https://github.com/nelsonenzo/tmux-appimage/releases).

### Red Hat Enterprise Linux / CentOS RPMs

The tmux packages available from the main repositories are often quite out of
date, especially for long-term support distributions. RPMs for newer tmux
versions can be obtained [from here](http://galaxy4.net/repo/).

For example to set up a repository and install on RHEL8:

~~~~
sudo yum install http://galaxy4.net/repo/galaxy4-release-8-current.noarch.rpm
sudo yum install tmux
~~~~

Or to install an RPM directly on RHEL6:

~~~~
sudo rpm -ivh http://galaxy4.net/repo/RHEL/6/x86_64/tmux-3.1b-2.el6.x86_64.rpm
~~~~

The repository method is recommended to automatically receive future package
updates. See [this page](https://anni.galaxy4.net/?page_id=39) for more
details.

## Cheat sheet

The tmux cheat sheet quick reference of most commonly used shortcuts and commands

### New session
Start a new session
```bash
$ tmux
```
Start a new named session
```bash
$ tmux new -s myname
```
Show all sessions
```bash
$ tmux ls
```

### Attach session
Attach to last session
```bash
$ tmux a
```
Attach to named
```bash
$ tmux a -t myname
```


### Kill session
Kill a session by name
```bash
$ tmux kill-ses -t myname
```
Kill sessions but the current
```bash
$ tmux kill-ses -a
```
Kill sessions but 'myname'
```bash
$ tmux kill-ses -a -t myname
```


### Tmux help
```bash
$ tmux info
```

### Config
Reload config
```bash
$ tmux source-file ~/.tmu­x.conf
```
Show config
```bash
$ tmux show-options -g
```



### Copy Mode  
| Command      | Description                |
|--------------|----------------------------|
| `Ctrl+b` `[` | Enter copy mode            |
| `<Space>`    | Start selection            |
| `Enter`      | Copy selection             |
| `q`          | Quit copy mode             |
| `Ctrl+b` `]` | Paste contents of buffer_0 |


Mainly works like selecting text in [Vim](../text/vim.md#motions)


## Tmux shortcuts

### Getting started
| Shortcuts    | Description        |
|--------------|--------------------|
| `Ctrl+b` `?` | List all shortcuts |

<br/>

Show every session, window, pane, etc.
```bash
$ tmux info
```

### Panes (Splits)

| Shortcuts              | Description        |
|------------------------|--------------------|
| `Ctrl+b` `"` _/_ `%`   | Split Horiz/Vert   |
| `Ctrl+b` `!`           | Pane -> Window     |
| `Ctrl+b` `x`           | Kill pane          |
| `Ctrl+b` <Arrow\>      | Navigate panes     |
| `Ctrl+b` <Space\>      | Toggle layouts     |
| `Ctrl+b` `{` _/_ `}`   | Move to Left/Right |
| `Ctrl+b` `o`           | Goto next panes    |
| `Ctrl+b` `z`           | toggle full-screen |
| `Ctrl+b` `;`           | Toggle Last pane   |
| `Ctrl+b` `q`           | Show numbers       |
| `Ctrl+b` `q` `0`...`9` | Goto # pane        |


### Window (Tabs)
|                      | Description          |
|----------------------|----------------------|
| `Ctrl+b` `c`         | Create window        |
| `Ctrl+b` `p` _/_ `n` | Previous/Next window |
| `Ctrl+b` `"` _/_ `%` | Split Horiz/Vert     |
| `Ctrl+b` `w`         | List window          |
| `Ctrl+b` `,`         | Rename window        |
| `Ctrl+b` `f`         | Find window          |
| `Ctrl+b` `l`         | Last window          |
| `Ctrl+b` `.`         | Move window          |
| `Ctrl+b` `&`         | Close window         |
| `Ctrl+b` `0`...`9`   | Goto # window        |



### Session (Set of Windows)
| -                    | Description                    |
|----------------------|--------------------------------|
| `Ctrl+b` `d`         | <red>Detach from session</red> |
| `Ctrl+b` `s`         | Show all sessions              |
| `Ctrl+b` `$`         | Rename session                 |
| `Ctrl+b` `(` _/_ `)` | Previous/Next session          |


## Tmux Command Mode

### Usage
| Command      | Description        |
|--------------|--------------------|
| `Ctrl+b` `:` | Enter command mode |

### Resizing 

| Command             | Description  |
|---------------------|--------------|
| `resize-pane -D 20` | Resize down  |
| `resize-pane -U 20` | Resize up    |
| `resize-pane -L 20` | Resize left  |
| `resize-pane -R 20` | Resize right |


### Listing

| Command        | Description  |
|----------------|--------------|
| `list-keys`    | All commands |
| `list-panes`   | All panes    |
| `list-windows` | All Windows  |

### Copying

| Command              | Description      |
|----------------------|------------------|
| `list-buffers`       | List all buffers |
| `show-buffer`        | Show #0 contents |
| `capture-pane`       | Copy of pane     |
| `choose-buffer`      | Show and paste   |
| `save-buffer a.txt`  | Save to file     |
| `delete-buffer -b 1` | Delete buffer 1  |


### Setting
| Command               | Description           |
|-----------------------|-----------------------|
`set -g OPTION` | Set for all sessions
`setw -g OPTION` | Set for all windows
`setw -g mode-keys vi` | Enable vi-mode
`set -g prefix C-a` | Set prefix


### Misc
| Command                  | Description  |
|--------------------------|--------------|
| `swap-pane -s 3 -t 1`    | Swap pane    |
| `swap-window -t -1`      | Move to left |
| `setw synchronize-panes` | Sync Panes   |
| `join-pane -t :#`        | Join pane    |

## Example tmux session

An example tmux session from the [MusicPlayerPlus](../projects/MusicPlayerPlus.md) project:

```bash
#!/bin/bash
#
# mpcplus-tmux - run the mpcplus MPD client, spectrum visualizer using tmuxp

export SESSION=musicplayerplus

if [ -f ${HOME}/.config/mpcplus/config ]
then
  MPCDIR="${HOME}/.config/mpcplus"
else
  if [ -f ${HOME}/.mpcplus/config ]
  then
    MPCDIR="${HOME}/.mpcplus"
  else
    mppinit
    MPCDIR="${HOME}/.config/mpcplus"
  fi
fi

usage() {
  printf "\nUsage: mpcplus-tmux [-a] [-A] [-c client] [-g] [-p script] [-r] [-u]"
  printf "\nWhere:"
  printf "\n\t-a indicates display album cover art using tmuxp"
  printf "\n\t-A indicates disable display of album cover art"
  printf "\n\t-c client specifies an MPD client to run in the client pane"
  printf "\n\t\tAlbum cover art display is only supported for mpcplus and ncmpcpp"
  printf "\n\t-g indicates do not use gradient colors for spectrum visualizer"
  printf "\n\t-p script specifies an asciimatics script to run"
  printf " in the visualizer pane"
  printf "\n\t-r indicates record tmux session with asciinema"
  printf "\n\t-u displays this usage message and exits\n"
  printf "\nDefaults: cover art enabled, ascii art disabled, recording disabled"
  printf "\nThis run:"
  if [ "${PYART}" ]
  then
    printf "\n\tascii art enabled"
  else
    printf "\n\tascii art disabled"
  fi
  if [ "${RECORD}" ]
  then
    printf "\n\trecording enabled"
  else
    printf "\n\trecording disabled"
  fi
  printf "\nType 'man mpcplus-tmux' for detailed usage info on mpcplus-tmux"
  printf "\nType 'man mpcplus' for detailed usage info on the mpcplus MPD client\n"
  exit 1
}

start_tmux_session() {
  tmux new-session -d -x "$(tput cols)" -y "$(tput lines)" -s ${SESSION}
  tmux set -g status off
  tmux send-keys "stty -echo" C-m
  tmux send-keys "tput civis -- invisible" C-m
  tmux send-keys "export PS1=''" C-m
  tmux send-keys "clear" C-m
  tmux send-keys "${MPPCOMM}; exit" C-m
  tmux split-window -v -p ${V_HEIGHT}
  tmux send-keys "${VIZCOMM}; exit" C-m
  tmux select-pane -t 1
  tmux a #
}

MPP_ENV_MODE=unknown
USE_GRAD=1
USE_ART=1
PYART=
RECORD=
USAGE=
V_HEIGHT=30
CLIENT_COMM=mpcplus
USE_MPCPLUS=1
ALT_SCRIPT="${MPCDIR}/ueberzug/mpcplus-ueberzug"
ARGS="$*"
while getopts "aAc:gm:p:ru" flag; do
    case $flag in
        a)
          USE_TMUXP=1
          ;;
        A)
            USE_ART=
          ;;
        c)
          CLIENT_COMM=${OPTARG}
          USE_MPCPLUS=
          client_name=`echo "${CLIENT_COMM}" | awk ' { print $1 } '`
          client_name=`basename ${client_name}`
          [ "${client_name}" == "mpcplus" ] || [ "${client_name}" == "ncmpcpp" ] || {
            USE_ART=
          }
          ;;
        g)
          USE_GRAD=
          ;;
        m)
          MPP_ENV_MODE=${OPTARG}
          ;;
        p)
          PYART=${OPTARG}
          ;;
        r)
          have_nema=`type -p asciinema`
          [ "${have_nema}" ] && RECORD=1
          ;;
        u)
          USAGE=1
          ;;
    esac
done
shift $(( OPTIND - 1 ))

have_tmuxp=`type -p tmuxp`
[ "${have_tmuxp}" ] || USE_TMUXP=

[ "${USAGE}" ] && usage

export MPP_ENV_MODE

if [ "${DISPLAY}" ]
then
  consolemode=
  # Check if on a console screen
  have_tty=`type -p tty`
  [ "${have_tty}" ] && {
    tty=$(tty)
    echo "${tty}" | grep /dev/tty > /dev/null && consolemode=1
    echo "${tty}" | grep /dev/con > /dev/null && consolemode=1
  }
  [ "${consolemode}" ] || {
    # Check if this is an SSH session
    [ -n "$SSH_CLIENT" ] || [ -n "$SSH_TTY" ] && consolemode=1
  }
  [ "${consolemode}" ] && USE_ART=
else
  USE_ART=
fi

numrows=`tput lines`
MAIN_PANE_HEIGHT=$((2 * ${numrows} / 3))

if [ "${USE_ART}" ]
then
  if [ "${USE_MPCPLUS}" ]
  then
    MPPCOMM="${ALT_SCRIPT}"
  else
    MPPCOMM="${ALT_SCRIPT} -c '${CLIENT_COMM}'"
  fi
else
  MPPCOMM="${CLIENT_COMM}"
fi
if [ "${USE_GRAD}" ]
then
  VIZCOMM="mppcava"
else
  VIZCOMM="mppcava -p ${HOME}/.config/mppcava/config-tmux"
fi
[ "${PYART}" ] && {
  have_pyart=`type -p mpp${PYART}`
  [ "${have_pyart}" ] && {
    VIZCOMM="mpp${PYART}"
    V_HEIGHT=50
    MAIN_PANE_HEIGHT=$((${numrows} / 2))
  }
}
export MAIN_PANE_HEIGHT MPPCOMM VIZCOMM

sleep 1
if [ "${USE_TMUXP}" ]
then
  tmuxp load mpcplus-env
else
  start_tmux_session
fi

[ "${RECORD}" ] && {
  tmux d
  VID_DIR=$HOME/Videos
  [ -d ${VID_DIR} ] || mkdir ${VID_DIR}
  REC_DIR=${VID_DIR}/asciinema
  [ -d ${REC_DIR} ] || mkdir ${REC_DIR}
  echo "Recording this ${SESSION} session with asciinema"
  asciinema rec --command "tmux attach -t ${SESSION}" ${REC_DIR}/${SESSION}-$(date +%F--%H%M).cast
}
```

## Example tmux configuration

The tmux configuration file `tmux.conf`:

```
## Custom key bindings

# Switch windows using Alt-PgDn and Up without prefix
# bind-key -n M-Right next-window
# bind-key -n M-Left  previous-window
# bind-key -n M-n     next-window
# bind-key -n M-p     previous-window
bind-key -n M-PgDn next-window
bind-key -n M-PgUp previous-window

# Switch panes using Alt-arrow without prefix
bind-key -n M-Left select-pane -L
bind-key -n M-Right select-pane -R
bind-key -n M-Up select-pane -U
bind-key -n M-Down select-pane -D

# Resize panes
# bind-key -r C-Left resize-pane -L 5
# bind-key -r C-Right resize-pane -R 5
# bind-key -r C-Up resize-pane -U 2
# bind-key -r C-Down resize-pane -D 2

# Exit session
bind-key -n M-x confirm-before -p "kill-session #S? (y/n)" kill-session
bind-key -n M-X kill-session
bind-key q confirm-before -p "kill-session #S? (y/n)" kill-session
bind-key Q kill-session

# Remap prefix from 'C-b' to 'C-a'
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix

# Reload config file
bind-key r source-file ~/.tmux.conf\; display ' Reloaded tmux config.'

# Split panes using | and -
bind-key | split-window -h -c '#{pane_current_path}'
bind-key - split-window -v -c '#{pane_current_path}'
unbind '"'
unbind %

# Shift + arrow key to move between windows
bind-key -n S-Left  previous-window
bind-key -n S-Right next-window

# Sync panes
bind-key s set-window-option synchronize-panes

## Window options

# 1-indexed panes to match the windows
set-window-option -g pane-base-index 1

# Increase history buffer
set-window-option -g history-limit 1000000

# default window title colors
set-window-option -g window-status-style fg=colour244,bg=default #base0 and default
#set-window-option -g window-status-style dim
#set-window-option -g window-status-style 'fg=colour9 bg=colour18'
#set-window-option -g window-status-format ' #I#[fg=colour237]:#[fg=colour250]#W#[fg=colour244]#F '

# active window title colors
set-window-option -g window-status-current-style fg=colour166,bg=default #orange and default
#set-window-option -g window-status-current-style bright
#set-window-option -g window-status-current-style 'fg=colour1 bg=colour19 bold'
#set-window-option -g window-status-current-format ' #I#[fg=colour249]:#[fg=colour255]#W#[fg=colour249]#F '

# bell
set-window-option -g window-status-bell-style fg=colour235,bg=colour160 #base02, red

# be aggressive
set-window-option -g aggressive-resize on

## General options

# 0 is too far from Ctrl-a
set-option -g base-index 1

# Enable mouse mode (tmux 2.1 and above)
set-option -g mouse on

# Status bar
# set-option -g status-interval 30
# set-option -g status-fg colour249
# set-option -g status-bg colour238
set-option -g status-position bottom
set-option -g status-justify left
# Status Left
set-option -g status-left-length 50
# set-option -g status-left-length 20
# set-option -g status-left ''
# set-option -g status-left '#H #{?client_prefix,#[bg=colour10 fg=colour0] Ctrl #[default] ,}'
set-option -g status-left '#{?client_prefix,#[bg=colour10 fg=colour0] Ctrl #[default] ,}'
# Status Right
set-option -g status-right-length 100
# set-option -g status-right-length 50
# set-option -g status-right '#(uptime -p | sed "s/ years\?,/y/;s/ weeks\?,/w/;s/ days\?,/d/;s/ hours\?,/h/;s/ minutes\?/m/"), #[fg=colour255]#(hostname -I | sed "s/ / \/ /;s/ *$//g"),#[default] #(cut -d " " -f 1-3 /proc/loadavg), #[fg=colour255]%H:%M:%S'
# set-option -g status-right '#[fg=colour233,bg=colour19] %d/%m #[fg=colour233,bg=colour8] %H:%M:%S '
set-option -g status-right "#[fg=cyan]%A, %d %b %Y %I:%M %p"
# Status bar colors
# set-option -g status-style bg=default
# set-option -g status-style fg=colour136,bg=colour235 #yellow and base02
# yellow with transparent background
set-option -g status-style fg=colour136,bg=default

# Messages
set-option -g message-style fg=colour166,bg=colour235 #orange and base02
set-option -g display-time 1000

# Repeat time increase
set-option -g repeat-time 1000

# Terminal
#
# If xterm-24bit terminal type has been set,
# configure tmux for 24 bit color support
# Uncomment these two lines for 24 bit color
# set-option -g default-terminal "xterm-24bit"
# set-option -ga terminal-overrides ',*-24bit:Tc'

# These enable 256 color terminal in tmux
# Comment these two lines out if above 24 bit color terminal was enabled
set-option -g default-terminal "xterm-256color"
set-option -ga terminal-overrides ',*-256color*:Tc'

# pane border
set-option -g pane-border-style fg=colour235 #base02
set-option -g pane-active-border-style fg=colour240 #base01
# set-option -g pane-border-style fg=blue,bg=default
# set-option -g pane-active-border-style fg=green,bg=default
# set-option -g pane-border-format '#[align=right]#{?pane_active,#[fg=white bg=colour22],#[fg=default]} #{window_name}:#{pane_index} #{pane_current_command} #{pane_current_path} #[default]'
# set-option -g pane-border-status top

# pane number display
set-option -g display-panes-active-colour colour33 #blue
set-option -g display-panes-colour colour166 #orange

# quiet
set-option -g visual-activity off
set-option -g visual-bell off
set-option -g visual-silence off
set-option -g bell-action none
set-window-option -g monitor-activity off
```

## See also

- [iTerm2](iterm2.md)
- [Kitty](kitty/kitty.md)
- [Screen](screen.md)
