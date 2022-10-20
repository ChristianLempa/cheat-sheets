---
tags:
    - shell
    - linux
    - plugins
    - zsh
categories:
    - shells
    - plugins
---

# External plugins

## A list of plugins that don't come bundled with Oh My Zsh

There is no restriction for adding your plugin into zsh bundle (unlike [themes](https://github.com/ohmyzsh/ohmyzsh/wiki/External-themes)) but the rationale for creating this page is next:

* sometimes you're not really sure if your plugin will not harm (e.g. it can break something).

### Installation

It should be clear from [this](https://github.com/ohmyzsh/ohmyzsh/wiki/Customization#overriding-and-adding-plugins).

### The plugins

#### Custom git plugin

Fixes some inconsistencies in the default git plugin that make the aliases more intuitive, while adding some other useful functions.

You can get it from [here](https://github.com/davidde/git).

#### Git auto status

If you found yourself constantly typing `git status` after bunch of commands like
`git commit` and you want to avoid that, then this plugin is for you.

This plugin is a nice addition to **git_prompt_status**.

You can get it from [here](https://gist.github.com/oshybystyi/475ee7768efc03727f21).

#### History Sync

GPG encrypted, Internet synchronized Zsh history using Git.

You can get it from [here](https://github.com/wulfgarpro/history-sync).

#### Doge Say

Get a doge to repeat every command you put in!

See it in action:

![Alt Text](https://raw.githubusercontent.com/txstc55/dogesay/master/dogesay.gif)

And get your doge [here](https://github.com/txstc55/dogesay/blob/master/dogesay.plugin.zsh).

#### fz

Give tab-completions to `z`.

[![fz demo](https://github.com/changyuheng/fz/raw/master/fz-demo.gif)](https://github.com/changyuheng/fz/blob/master/fz-demo.gif)

Get it [here](https://github.com/changyuheng/fz).

#### aterminal

**Homepage:** https://github.com/guiferpa/aterminal
**Maintainer:** [guiferpa](https://github.com/guiferpa)

##### Description

This plugin show platforms version

##### Support

[Nodejs](https://nodejs.org), [NPM](https://www.npmjs.com), [Docker](https://www.docker.com), [Go](https://golang.org), [Python](https://www.python.org), [Elixir](https://elixir-lang.org) and [Ruby](https://www.ruby-lang.org)

##### Demo

![Demo](https://raw.githubusercontent.com/guiferpa/aterminal/master/images/demo.gif)

#### [xxh](https://github.com/xxh/xxh) - bring Oh My Zsh wherever you go through the SSH

Some users may want to use Oh My Zsh during the SSH connections. There is [xxh project](https://github.com/xxh/xxh) that allows bring Zsh with Oh My Zsh framework to the remote host without any installations, root access or affection on the host.

#### [zshnotes](https://github.com/jameshgrn/zshnotes)

A small, tidy, lightweight notes app that creates a daily text file and timestamps every line of added text

## See also

- [Oh My Zsh Github](https://github.com/ohmyzsh/ohmyzsh)
- [Zsh](../zsh.md)
