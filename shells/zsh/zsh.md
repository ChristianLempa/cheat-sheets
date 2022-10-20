---
tags:
    - shell
    - bash
    - sh
    - echo
    - script
    - linux
categories:
    - shells
---

# Zsh

The Z shell (Zsh) is a Unix shell that can be used as an interactive login shell and as a command interpreter for shell scripting. Zsh is an extended Bourne shell with many improvements, including some features of [Bash](../bash.md), [ksh](../ksh.md), and [tcsh](../tcsh.md).

Zsh is mostly compatible with Bash, so most everything in [Bash's cheatsheet](../bash.md) also applies.

Zsh has a robust and active community providing many useful enhancements and extensions. One very poplular Zsh community has formed around the [Oh My Zsh project](ohmyzsh/OhMyZsh.md).

Repository: https://sf.net/p/zsh/code/

Website: https://www.zsh.org/

## Expressions

| Expression  | Example | Description |
|-------------|---------|-------------|
| !!          | sudo !! | Last command (sudo !!) |
| !*          | vim !* | Last command's parameters (vim !*) |
| !^          |         | Last command's first parameter |
| !$          |         | Last command's last parameter |
| !?ls <tab>  | sudo !?mv <tab> | Command and params of last ls command |
| !?ls?:* <tab> |         | Params of last ls command |
| *(m0)         | rm *(m0) | Last modified today |
| *(m-4)        |         | Last modified <4 days ago |

## Change default shell

```shell
chsh -s `which zsh`
```

## Process Substitution

| Expression  | Example | Description |
|-------------|---------|-------------|
| <(COMMAND)  | grep "needle" <(curl "https://haystack.io")  | Replace argument with named pipe/FIFO (read-only) with command output |
| =(COMMAND)  | vim =(curl "https://haystack.io")  | Replace argument with file (writable) containing command output |

## Command Syntax

### A plain old glob
```shell
print -l *.txt
print -l **/*.txt
```

### Show text files that end in a number from 1 to 10
```shell
print -l **/*<1-10>.txt
```

### Show text files that start with the letter a
```shell
print -l **/[a]*.txt
```

### Show text files that start with either ab or bc
```shell
print -l **/(ab|bc)*.txt
```

### Show text files that don't start with a lower or uppercase c
```shell
print -l **/[^cC]*.txt
```

### Show only directories
```shell
print -l **/*(/)
```

### Show only regular files
```shell
print -l **/*(.)
```

### Show empty files
```shell
print -l **/*(L0)
```

### Show files greater than 3 KB
```shell
print -l **/*(Lk+3)
```

### Show files modified in the last hour
```shell
print -l **/*(mh-1)
```

### Sort files from most to least recently modified and show the last 3
```shell
print -l **/*(om[1,3])
```

### `.` show files, `Lm-2` smaller than 2MB, `mh-1` modified in last hour,
### `om` sort by modification date, `[1,3]` only first 3 files
```shell
print -l **/*(.Lm-2mh-1om[1,3])
```

### Show every directory that contain directory `.git`
```shell
print -l **/*(e:'[[ -d $REPLY/.git ]]':)
```

### Return the file name (t stands for tail)
```shell
print -l *.txt(:t)
```

### Return the file name without the extension (r stands for remove_extension)
```shell
print -l *.txt(:t:r)
```

### Return the extension
```shell
print -l *.txt(:e)
```

### Return the parent folder of the file (h stands for head)
```shell
print -l *.txt(:h)
```

### Return the parent folder of the parent
```shell
print -l *.txt(:h:h)
```

### Return the parent folder of the first file
```shell
print -l *.txt([1]:h)
```

### Parameter expansion
```shell
files=(*.txt)          # store a glob in a variable
print -l $files
print -l $files(:h)    # this is the syntax we saw before
print -l ${files:h}
print -l ${files(:h)}  # don't mix the two, or you'll get an error
print -l ${files:u}    # the :u modifier makes the text uppercase
```

### :s modifier
```shell
variable="path/aaabcd"
echo ${variable:s/bc/BC/}    # path/aaaBCd
echo ${variable:s_bc_BC_}    # path/aaaBCd
echo ${variable:s/\//./}     # path.aaabcd (escaping the slash \/)
echo ${variable:s_/_._}      # path.aaabcd (slightly more readable)
echo ${variable:s/a/A/}      # pAth/aaabcd (only first A is replaced)
echo ${variable:gs/a/A/}     # pAth/AAAbcd (all A is replaced)
```

### Split the file name at each underscore
```shell
echo ${(s._.)file}
```

### Join expansion flag, opposite of the split flag.
```shell
array=(a b c d)
echo ${(j.-.)array} # a-b-c-d
```

### Short if
```shell
if [[ ... ]] command
if [[ ... ]] { command ... }
```

### Short for
```shell
for i ( word ... ) command
for i ( word ... ) { command ... }
for i in word ... ; command
```

### Short while/until
```shell
while [[ ... ]] { command ... }
until [[ ... ]] { command ... }
```

### Use output of command, when using pipe is not possible
```shell
<( command )
```

### Similar to <( ), but creates temporary file (instead of FD or FIFO), when
### program needs to seek in output.
```shell
=( command )
```

### Start an interactive shell session:
```shell
zsh
```

### Execute a command and then exit:
```shell
zsh -c "command"
```

### Execute a script:
```shell
zsh path/to/script.zsh
```

### Execute a script, printing each command before executing it:
```shell
zsh --xtrace path/to/script.zsh
```

### Start an interactive shell session in verbose mode, printing each command before executing it:
```shell
zsh --verbose
```

### Execute a specific command inside `zsh` with disabled glob patterns:
```shell
noglob command
```

## See also

- [Oh My Zsh](ohmyzsh/OhMyZsh.md).
- [Powerlevel10k Zsh theme](powerlevel10k.md)
- [Bash](../bash.md)
- [Regular expressions](../../linux/regex.md)
