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

# Plugins Overview

- [Productivity](#productivity)
- [Password Managers](#password-managers)
- [FS jumping](#fs-jumping)
- [Build tools](#build-tools)
- [Node JS](#node-js)
- [PHP](#php)
- [Ruby](#ruby)
- [Python](#python)
- [Distro-related](#distro-related)
- [macOS](#macos)
- [Misc](#misc)

## Productivity

| Name                                                                                                        | Description                                                                                                    |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| [ag](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/ag)                                             | autocomplettion for ag                                                                                         |
| [aliases](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/aliases)                                   | aliases cheatsheet - list aliases based on the plugins that you have enabled                                   |
| [autoenv](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/autoenv)                                   | automatically execs script on changing dir (.env file)                                                         |
| [colemak](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/colemak)                                   | colemak layout support + vi-mode fixes for colemak https://en.wikipedia.org/wiki/Keyboard_layout#Colemak       |
| [colored-man-pages](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/colored-man-pages)               | adds colors to manpages                                                                                        |
| [colorize](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/colorize)                                 | cat with syntax highlight support                                                                              |
| [command-not-found](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/command-not-found)               | suggests package name with relevant command                                                                    |
| [compleat](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/compleat)                                 | reformats completion https://github.com/mbrubeck/compleat                                                      |
| [copydir](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/copydir)                                   | copies current dir full path to clipboard                                                                      |
| [copyfile](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/copyfile)                                 | copies selected file content to clipboard                                                                      |
| [cp](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/cp)                                             | cp with progress bar (rsync)                                                                                   |
| [dircycle](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/dircycle)                                 | hotkeys for cycling directories                                                                                |
| [dirpersist](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/dirpersist)                             | saves and restores your directory stack across shell invocations                                               |
| [encode64](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/encode64)                                 | e64 & d64 aliases                                                                                              |
| [extract](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/extract)                                   | 'x' alias - swiss knife for archive extracting                                                                 |
| [fbterm](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/fbterm)                                     | enhanced VESA terminal https://code.google.com/p/fbterm/                                                       |
| [genpass](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/genpass)                                   | Three distinct 128-bit password generators                                                                     |
| [gpg-agent](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/gpg-agent)                               | gpg-agent start/stop funcs                                                                                     |
| [history](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/history)                                   | aliases: h for history, hsi for grepping history                                                               |
| [history-substring-search](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/history-substring-search) | implementation of fish history substring search                                                                |
| [kate](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/kate)                                         | Kate text editor alias https://kate-editor.org/                                                                |
| [last-working-dir](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/last-working-dir)                 | same as dirpersist                                                                                             |
| [mosh](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/mosh)                                         | mobile shell with roaming (wifi, mobile networks) and local echo https://mosh.mit.edu/                         |
| [pass](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pass)                                         | pass utility autocompletion                                                                                    |
| [per-directory-history](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/per-directory-history)       | self-descriptive                                                                                               |
| [profiles](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/profiles)                                 | different zsh profiles per hostname                                                                            |
| [rsync](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rsync)                                       | aliases                                                                                                        |
| [safe-paste](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/safe-paste)                             | extended copy/paste in terminal                                                                                |
| [screen](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/screen)                                     | GNU screen enhances (titles etc)                                                                               |
| [sprunge](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sprunge)                                   | CLI pastebin service sprunge.us uploader (https://www.shellperson.net/sprunge-pastebin-script/)                |
| [ssh-agent](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/ssh-agent)                               | ssh-agent start script                                                                                         |
| [sublime](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sublime)                                   | aliases for SublimeText Editor                                                                                 |
| [supervisor](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/supervisor)                             | autocompletion for https://supervisord.org                                                                     |
| [taskwarrior](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/taskwarrior)                           | autocompletion for https://taskwarrior.org                                                                     |
| [terminitor](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/terminitor)                             | **[RENAMED to consular]** Consular automates your development workflow setup https://github.com/achiu/consular |
| [tmux](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/tmux)                                         | enhanced Tmux support                                                                                          |
| [tmuxinator](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/tmuxinator)                             | enhanced Tmux support                                                                                          |
| [torrent](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/torrent)                                   | magnet2torrent converter function                                                                              |
| [tugboat](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/tugboat)                                   | Digital Ocean droplet manager                                                                                  |
| [urltools](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/urltools)                                 | urlencode/urldecode etc                                                                                        |
| [vi-mode](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/vi-mode)                                   | self descriptive                                                                                               |
| [vundle](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/vundle)                                     | Vim plugin manager https://github.com/gmarik/vundle                                                            |
| [wakeonlan](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/wakeonlan)                               | funcs for wakeonlan tool                                                                                       |
| [web-search](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/web-search)                             | google from CLI                                                                                                |

## Password Managers

| Name                                                                          | Description                                  |
| ----------------------------------------------------------------------------- | -------------------------------------------- |
| [1password](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/1password) | adds integration with 1password              |
| [genpass](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/genpass)     | provides various password generators         |
| [pass](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pass)           | completion for pass CLI password manager     |
| [rbw](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rbw)             | adds completion for rbw, a CLI for Bitwarden |

## FS Jumping

| Name                                                                        | Description                                                                                                   |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [autojump](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/autojump) | shell extension to jump to frequently used directories                                                        |
| [jump](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/jump)         | allows to mark dirs and jump to marks                                                                         |
| [pj](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pj)             | aliases for quick access to projects dir                                                                      |
| [wd](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/wd)             | yet another autojump tool github.com/mfaerevaag/wd                                                            |
| [z](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/z)               | yet another autojump                                                                                          |
| [zoxide](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/zoxide)     | a blazing fast, fully featured autojumper written in Rust ([homepage](https://github.com/ajeetdsouza/zoxide)) |

## Build tools

| Name                                                                                  | Description                                                                               |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| [ant](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/ant)                     | Java build tool https://ant.apache.org/                                                   |
| [bower](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/bower)                 | Front-end package manager https://github.com/bower/bower                                  |
| [cabal](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/cabal)                 | Haskell package manager https://www.haskell.org/cabal/                                    |
| [cake](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/cake)                   | Cake build tool                                                                           |
| [coffee](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/coffee)               | CoffeeScript completion                                                                   |
| [cpanm](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/cpanm)                 | cpanminus get, unpack, build, install Perl modules https://github.com/miyagawa/cpanminus/ |
| [docker](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/docker)               | application shipment tool https://github.com/dotcloud/docker                              |
| [gas](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/gas)                     | small utility used to manage Git authors. https://github.com/walle/gas                    |
| [git](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git)                     | extras: git-extras gitfast git-flow git-flow-avh git-hubflow git-remote-branch            |
| [github](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/github)               | cli access, url shortener                                                                 |
| [gitignore](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/gitignore)         | git alias to fetch default .gitignore files from https://gitignore.io/                    |
| [gnu-utils](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/gnu-utils)         | GNU coreutils wrappers to override shell builtins                                         |
| [golang](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/golang)               | Go build tool https://golang.org/cmd/go/                                                  |
| [gradle](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/gradle)               | build automation tool https://www.gradle.org/                                             |
| [grails](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/grails)               | funcs for grails script management https://grails.org/                                    |
| [heroku](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/heroku)               | cli access https://www.heroku.com/                                                        |
| [jira](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/jira)                   | JIRA cli access                                                                           |
| [knife](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/knife)                 | knife autocompletion                                                                      |
| [knife_ssh](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/knife_ssh)         | knife autocompletion                                                                      |
| [lein](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/lein)                   | leiningen autocompletion https://leiningen.org                                            |
| [lighthouse](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/lighthouse)       | CLI access to issue tracker Lighthouse, https://lighthouseapp.com/                        |
| [mercurial](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/mercurial)         | hg autocompletion                                                                         |
| [mix](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/mix)                     | Elixir build tool autocompletion https://elixir-lang.org/docs/stable/mix                  |
| [mvn](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/mvn)                     | maven completion                                                                          |
| [nanoc](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/nanoc)                 | static website generator https://nanoc.ws/                                                |
| [postgres](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/postgres)           | aliases for Postgres managing                                                             |
| [perl](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/perl)                   | aliases for Perl                                                                          |
| [rebar](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rebar)                 | Erlang build tool autocompletion                                                          |
| [redis-cli](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/redis-cli)         | Redis autocompletion                                                                      |
| [repo](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/repo)                   | git repo management tool autocompletion https://code.google.com/p/git-repo/               |
| [sbt](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sbt)                     | autocomplete for ScalaBuildTool https://www.scala-sbt.org/                                |
| [scala](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/scala)                 | autocomplete                                                                              |
| [sfffe](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sfffe)                 | aliases for ack (JS & CSS grepping) https://beyondgrep.com/                               |
| [svn](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/svn)                     | subversion autocompletion                                                                 |
| [svn-fast-info](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/svn-fast-info) | faster subversion autocompletion (especially interesting on big project)                  |
| [vagrant](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/vagrant)             | quick development env deployment https://www.vagrantup.com/                               |

## Node JS

| Name                                                                          | Description                                        |
| ----------------------------------------------------------------------------- | -------------------------------------------------- |
| [jake-node](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/jake-node) | NodeJS build tool Jake https://github.com/mde/jake |
| [node](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/node)           | NodeJS docs easy access via CLI                    |
| [npm](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/npm)             | package manager for NodeJS                         |
| [nvm](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/nvm)             | NodeJS version manager                             |

## PHP

| Name                                                                        | Description                                                                    |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [composer](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/composer) | PHP dependency manager https://getcomposer.org                                 |
| [laravel](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/laravel)   | PHP deployment tool artisan completion https://laravel.com/docs/master/artisan |
| [phing](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/phing)       | Ant-like build system for PHP https://phing.info                               |
| [symfony](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/symfony)   | PHP webframework https://symfony.com                                           |
| [symfony2](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/symfony2) | PHP webframework https://symfony.com                                           |
| [yii](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/yii)           | PHP webframework https://yiiframework.com                                      |
| [yii2](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/yii2)         | PHP webframework https://yiiframework.com                                      |

## Ruby

| Name                                                                            | Description                                                               |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| [bundler](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/bundler)       | package manager https://bundler.io/                                       |
| [capistrano](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/capistrano) | remote deployment tool                                                    |
| [gem](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/gem)               | https://rubygems.org/                                                     |
| [jruby](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/jruby)           | JRuby aliases                                                             |
| [pow](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pow)               | rack apps restarter https://pow.cx/                                       |
| [powder](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/powder)         | powder gem autocompletion https://github.com/Rodreegez/powder             |
| [powify](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/powify)         | another pow manager https://github.com/sethvargo/powify                   |
| [rails](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rails)           | rails aliases for rails 2, rails 3, and rails 4 all in one clean plugin   |
| [rake](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rake)             | Ruby build tool                                                           |
| [rbenv](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rbenv)           | Ruby version switcher                                                     |
| [rbfu](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rbfu)             | **[OBSOLETE]** another Ruby version manager https://github.com/hmans/rbfu |
| [ruby](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/ruby)             | aliases                                                                   |
| [rvm](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rvm)               | another RubyVersionManager                                                |
| [thor](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/thor)             | Ruby doc tool https://github.com/erikhuda/thor                            |
| [zeus](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/zeus)             | funcs for Zeus (Rails env preloader) https://github.com/burke/zeus        |

## Python

| Name                                                                                          | Description                                                     |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| [celery](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/celery)                       | Python distributed task queue                                   |
| [fabric](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/fabric)                       | remote deployment tool https://docs.fabfile.org/en/1.8/         |
| [pip](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pip)                             | Python package manager https://www.pip-installer.org/en/latest/ |
| [python](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/python)                       | python aliases (pyfind, pyclean, pygrep)                        |
| [pyenv](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pyenv)                         | python version management                                       |
| [virtualenv](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/virtualenv)               | https://pypi.python.org/pypi/virtualenv isolated Python envs    |
| [virtualenvwrapper](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/virtualenvwrapper) | https://pypi.python.org/pypi/virtualenv isolated Python envs    |

## Distro-related

| Name                                                                          | Description                             |
| ----------------------------------------------------------------------------- | --------------------------------------- |
| [archlinux](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/archlinux) | aliases for yaourt and pacman           |
| [debian](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/debian)       | aliases for apt\* utils                 |
| [dnf](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/dnf)             | aliases for `dnf`                       |
| [suse](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/suse)           | aliases for SUSE Linux (zypper aliases) |
| [systemd](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/systemd)     | aliases                                 |
| [yum](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/yum)             | aliases                                 |

## macOS

| Name                                                                                        | Description                                                |
| ------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| [apache2-macports](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/apache2-macports) | apache management functions                                |
| [brew](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/brew)                         | package manager https://brew.sh/                           |
| [forklift](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/forklift)                 | macOS file browser                                         |
| [macports](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/macports)                 | macport autocompletion                                     |
| [macos](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/macos)                       | macOS completions and iTunes & Spotify control             |
| [mysql-macports](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/mysql-macports)     | same as apache-macport for MySQL                           |
| [pod](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pod)                           | https://cocoapods.org library dependency manager for Xcode |
| [textmate](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/textmate)                 | aliases                                                    |

## Misc

| Name                                                                              | Description                                                                     |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| [battery](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/battery)         | allows see battery status in PS                                                 |
| [emoji-clock](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/emoji-clock) | fancy shell clocks                                                              |
| [lol](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/lol)                 | dowant                                                                          |
| [rand-quote](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/rand-quote)   | quote function for random quotes from https://www.quotationspage.com/random.php |
| [themes](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/themes)           | ZSH theme switcher                                                              |

## See also

- [Oh My Zsh Github](https://github.com/ohmyzsh/ohmyzsh)
- [Zsh](../zsh.md)
