---
tags:
    - shell
    - linux
    - zsh
categories:
    - shells
---

# Cheatsheet

Quick reference:

- Oh My Zsh's Command-Line Interface (CLI): `omz`. Run `omz --help` for available commands.
- To **update** Oh My Zsh: `omz update`.
- To **uninstall** it: `uninstall_oh_my_zsh`.
- To apply changes made to `.zshrc`: `omz reload` (this just runs `exec zsh`).
  [**Do NOT run `source ~/.zshrc`**](https://github.com/ohmyzsh/ohmyzsh/wiki/FAQ#how-do-i-reload-the-zshrc-file).

## Commands

| Command         | Description                                                                                |
| :-------------- | :----------------------------------------------------------------------------------------- |
| `alias`         | List all aliases                                                                           |
| `mkcd` | Create a new directory and change to it, will create intermediate directories as required. |
| `take` | Like `mkcd`, but also knows how to handle remote URLs. When given an argument that looks like a URL (something that ends in `.git` or `.tar.(gz\|bz2\|xz)`), download the remote resource and extract it (if necessary) into the current directory. Then change to the newly extracted/downloaded/cloned directory. |
| `zsh_stats`     | Get a list of the top 20 commands and how many times they have been run.                   |

## Directory

| Alias      | Command                                    |
| :--------- | :----------------------------------------- |
| `md`       | `mkdir -p`                                 |
| `rd`       | `rmdir`                                    |
| `cd` / `~` | `cd` to your home directory                |
| `..`       | `cd ..`                                    |
| `...`      | `cd ../..`                                 |
| `....`     | `cd ../../..`                              |
| `.....`    | `cd ../../../..`                           |
| `/`        | `cd /`                                     |
| `d`        | `dirs -v` (lists last visited directories) |
| `cd +n`    | Switch to directory number `n`             |
| `-`        | `cd` to last visited directory             |
| `1`        | `cd -1`                                    |
| `2`        | `cd -2`                                    |
| `3`        | `cd -3`                                    |
| `4`        | `cd -4`                                    |
| `5`        | `cd -5`                                    |
| `6`        | `cd -6`                                    |
| `7`        | `cd -7`                                    |
| `8`        | `cd -8`                                    |
| `9`        | `cd -9`                                    |

## See also

- [Oh My Zsh Github](https://github.com/ohmyzsh/ohmyzsh)
- [Zsh](../zsh.md)
