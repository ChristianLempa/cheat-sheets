---
tags:
    - shell
    - linux
    - themes
    - zsh
categories:
    - shells
    - themes
---

# External themes

Due to the massive amount of themes bundled with OMZ, [new themes are not accepted](https://github.com/ohmyzsh/ohmyzsh/#do-not-send-us-themes). This is a list of other themes that are compatible with Oh My Zsh that live in their own separate repositories. More themes are listed in the [awesome-zsh-plugins](https://github.com/unixorn/awesome-zsh-plugins) list.

You can also use Github's search to find `*.zsh-theme` files:
[Gist zsh themes search](https://gist.github.com/search?l=Shell&q=extension%3Azsh-theme&ref=searchresults&utf8=%E2%9C%93), [GitHub zsh themes search](https://github.com/search?l=Shell&q=extension%3Azsh-theme+PS1+%7C%7C+PROMPT+&ref=searchresults&type=Code&utf8=%E2%9C%93).

## Installation

Check out the instructions [here](https://github.com/ohmyzsh/ohmyzsh/wiki/Customization#overriding-and-adding-themes).

---

### passion

![passion](https://raw.githubusercontent.com/ChesterYue/ohmyzsh-theme-passion/master/passion.gif)

* real time prompt.
* command running time cost prompt.
* command running error hint.

source: [Passion repo](https://github.com/ChesterYue/ohmyzsh-theme-passion)

author: [@chesteryue](https://github.com/ChesterYue)

---

<a href="https://github.com/reobin/typewritten"><p align="center">
  <img src="https://raw.githubusercontent.com/reobin/typewritten/main/docs/_media/logo.svg" alt="typewritten" />
</p></a>
<h3 align="center"><a href="https://github.com/reobin/typewritten">typewritten</a></h3>
<p align="center">A minimal zsh prompt</p>
<br />
<p align="center">
  <a href="https://github.com/reobin/typewritten/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/reobin/typewritten?style=flat-square" />
  </a>
  <a href="https://github.com/reobin/typewritten/releases">
    <img src="https://img.shields.io/github/v/release/reobin/typewritten?style=flat-square" />
  </a>
  <a href="https://npmjs.com/package/typewritten">
    <img src="https://img.shields.io/npm/dm/typewritten?style=flat-square&logo=npm" />
  </a>
</p>
<p align="center">
  <a href="https://github.com/reobin/typewritten/stargazers">
    <img src="https://img.shields.io/github/stars/reobin/typewritten?style=flat-square&logo=github" />
  </a>
  <a href="https://github.com/reobin/typewritten/network/members">
    <img src="https://img.shields.io/github/forks/reobin/typewritten?style=flat-square&logo=github" />
  </a>
  <a href="#contributors">
    <!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
    <img src="https://img.shields.io/badge/all_contributors-28-orange.svg?style=flat-square" alt="All contributors" />
<!-- ALL-CONTRIBUTORS-BADGE:END -->
  </a>
</p>
<a href="https://github.com/reobin/typewritten"><p align="center">
  <img src="https://raw.githubusercontent.com/reobin/typewritten/main/docs/_media/typewritten.gif" width="800" />
</p></a>

**Quick start**

```shell
npm install -g typewritten
# then reload zsh
```

**Features**

* Asynchronous git info
* 100% customizable
* Actively maintained
* [Thorough documentation](https://typewritten.dev)

Repository: [typewritten.zsh](https://github.com/reobin/typewritten)

Documentation: [typewritten.dev](https://typewritten.dev)

Author:  [@reobin](https://github.com/reobin)

---

<h3 align="center"><a href="https://github.com/Moarram/headline">Headline</a></h3>
<p align="center">A theme with Git status info and a colored line</p>
<br/>
<a href="https://github.com/Moarram/headline"><p align="center">
  <img src="https://raw.githubusercontent.com/moarram/headline/assets/images/demo.png" width="600"/>
</p></a>

**Features**

* Color matched separator line
* Dynamic information line
* Git status info (including commits ahead/behind)
* Customizable colors, styles, and symbols

Author: [@Moarram](https://github.com/moarram)

---

### yeknomhtooms

<img width="912" alt="smoothmonkey" src="https://user-images.githubusercontent.com/17438047/179404887-b1bdb0a7-9f73-46cf-bcad-a9ac6a98c4e0.png">

See [repository](https://github.com/sebastianpulido/oh-my-zsh) for source code.
Author: [@sebastianpulido](https://github.com/sebastianpulido)

---

### ubunly

The  **new Kali Linux**  console adapted to Ubuntu (and maybe any distro)!

> To install it, it is as easy as running the single INSTALLER.sh file.

* Install: [how to install](https://github.com/alejandromume/ubunly-zsh-theme#install)

* Source: [here](https://github.com/alejandromume/ubunly-zsh-theme)
* Author [@alejandromume](https://github.com/alejandromume)

---

### bigpath

![bigpath screenshot](https://preview.redd.it/ie39emm3bl461.png?width=1230&format=png&auto=webp&s=418d6c1a143bd4506bb3c161264606375ed5050e)

This theme can show your username, your current directory + the one before, git information (branch and unstaged/uncommited changes), and the current time.
Pink dot means unstaged, purple dot means uncommitted.

Author: [@Tesohh](https://github.com/Tesohh)
[Repo](https://github.com/Tesohh/omzbigpath)

---

### ✏️✅ emoji

emoji theme for [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh/). simplified *robbyrussell* and replaced git prompt symbol with emoji for better clarity. Works fine on Macs.

![Alt text](https://raw.githubusercontent.com/masaakifuruki/emoji.zsh-theme/main/emoji_theme_ohmyzsh.png "emoji oh my zsh theme preview")

#### Installation

Copy emoji.zsh-theme into your ```~/.oh-my-zsh/themes/``` directory

Then change current theme to emoji ```ZSH_THEME=emoji``` in your ```~/.zshrc```.

Activate a new theme with  ```$ source ~/.zshrc```.

#### Syntax

* ```➜ current_dir (git_branch) <emoji indicator>```

* ✏️ Git prompt is dirty (uncommitted files)
* ✅ Git prompt is clean (committed)

#### Issues

* ✏️ emoji is breaking cursor potion to the right hover on the first character on Crostini terminal

source: [repo](https://github.com/masaakifuruki/emoji.zsh-theme)

author: [@masaakifuruki](https://github.com/masaakifuruki)

---


### guezwhoz

![guezwhoz](https://github.com/guesswhozzz/guezwhoz-scheme/blob/main/demos/completer-zsh-demo.gif?raw=true)

* Single git status marker for Visual Studio Code and Git cli
* Interactive `Tab` completer

source: [repo](https://github.com/guesswhozzz/guezwhoz-zshell)

author: [@guesswhozzz](https://github.com/guesswhozzz)

---

### Aphrodite Theme

![Aphrodite Terminal Theme](https://user-images.githubusercontent.com/11278181/56094804-29972500-5edf-11e9-90a4-ffafdc58d3d7.png)

Minimalistic Aphrodite theme does not have any visual noise. Displays only the necessary information: current user, hostname, working directory, git branch if exists. Looks great both with dark and white terminals.

See [repository](https://github.com/win0err/aphrodite-terminal-theme) for source and installation instructions.
Author: [@win0err](https://github.com/win0err)

---

### MacOS Terminal

<h3 align="center"><a href="https://github.com/alejandromume/macos-zsh-theme">MacOS Terminal</a></h3>

<p align="center">
  <a href="https://github.com/alejandromume/macos-zsh-theme/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/alejandromume/macos-zsh-theme?style=flat-square" />
  </a>
<a href="https://github.com/alejandromume/macos-zsh-theme/stargazers">
    <img src="https://img.shields.io/github/stars/alejandromume/macos-zsh-theme?style=flat-square&logo=github" />
  </a>
</p>

<br>

The minimal MacOS terminal brought to ZSH

* Tested OS's: `Ubuntu 20.04` and `Windows 10 WSL`

<a href="https://github.com/alejandromume/macos-zsh-theme">
<img src="https://raw.githubusercontent.com/alejandromume/macos-zsh-theme-media/main/Preview2.png" />
</a>

---

**Features**

* Git Branch at right
* Last Login message
* Same format as MacOS

**Code**

* [Installation](https://github.com/alejandromume/macos-zsh-theme/#installation)
* [Source Code](https://github.com/alejandromume/macos-zsh-theme)

**Credits**

* Author: [@alejandromume](https://github.com/alejandromume)

---

### short

<img src=https://github.com/nikhilkmr300/omz-themes/blob/master/images/short.png width=640>

If long prompts annoy you, this theme is for you!
It does away with the long path after the username, and retains only the basename of the current working directory in the prompt.

Features:

* Colored input to shell to easily differentiate it from the output of commands.
* No annoying long prompts.
* Option to keep/hide the virtual environment name.
* Prominent alert on command exiting with non-zero code.

Source: [Repository](https://github.com/nikhilkmr300/omz-themes) (also contains other themes you might be interested in)

Author: [@nikhilkmr300](https://github.com/nikhilkmr300)

---

### matte-black-yellow

<img src=https://github.com/nikhilkmr300/omz-themes/blob/master/images/matte-black-yellow-line.png width=640>

Features:

* Colored input to shell to easily differentiate it from the output of commands.
* Current git branch being checked out indicated at the end of the prompt.
* Option to keep/hide the virtual environment name.
* Prominent alert on command exiting with non-zero code.
* Dashed line separating successive prompts.

Source: [Repository](https://github.com/nikhilkmr300/omz-themes) (also contains other themes you might be interested in)

Author: [@nikhilkmr300](https://github.com/nikhilkmr300)

---

### color-input

<img src=https://github.com/nikhilkmr300/omz-themes/blob/master/images/color-input-line.png width=640>

Features:

* Colored input to shell to easily differentiate it from the output of commands.
* Current git branch being checked out indicated at the end of the prompt.
* Option to keep/hide the virtual environment name.
* Prominent alert on command exiting with non-zero code.
* Dashed line separating successive prompts.

Source: [Repository](https://github.com/nikhilkmr300/omz-themes) (also contains other themes you might be interested in)

Author: [@nikhilkmr300](https://github.com/nikhilkmr300)

---

### zsh2000

![zsh2000 theme](https://raw.githubusercontent.com/maverick9000/zsh2000/master/demo.png)

Powerline looking zsh theme with rvm prompt, git status and branch, current time, user, hostname, pwd, exit status, root and background job status.

Influenced heavily by agnoster's theme and jeremyFreeAgent's theme

Author: [@maverick9000](https://github.com/maverick9000)

### Daivasmara

![Daivasmara Theme](https://raw.githubusercontent.com/Daivasmara/daivasmara.zsh-theme/master/media/Screenshot%20from%202020-04-30%2016-12-27.png)

Chill zsh-theme, personal take on smt

Source: [daivasmara.zsh-theme](https://github.com/Daivasmara/daivasmara.zsh-theme)

Author:  [@Daivasmara](https://github.com/Daivasmara)

---

### Ducula

![Ducula Theme](https://raw.githubusercontent.com/janjoswig/Ducula/master/ducula_showcase.png)

 * Job status: Indicates if jobs are running in the background :coffee: (idea from agnoster theme)
 * Username abbreviations: Uses a different username if the corresponding mapping was set (idea from dieter theme)
 * Hostname abbreviations: Uses a different hostname if the corresponding mapping was set (idea from dieter theme)
 * Virtual environments: Shows the name of activated virtual environment via ${VIRTUAL_ENV}
 * Current path: Displays the full current working directory
 * Return status: Shows the error return code (:bat:/:duck:)
 * Git messages: Uses `git_super_status` from the git-prompt plugin
 * Prompt time: Timestamp (hh:mm)

See [repository](https://github.com/janjoswig/Ducula) for source.  
Author: [@janjoswig](https://github.com/janjoswig/)

---

### Nuts Theme

![Nuts Terminal Theme](https://raw.githubusercontent.com/rafaelsq/nuts.zsh-theme/master/nuts.zsh-theme.png)

Branch name change color if code is modified.  
Arrow change color if exit code is not zero.  

See [github.com/rafaelsq/nuts.zsh-theme](https://github.com/rafaelsq/nuts.zsh-theme) for source.  
Author: [@rafaelsq](https://github.com/rafaelsq/)

---

### Reggae Theme

![Reggae Terminal Theme](https://i.imgur.com/lQaaWvX.png)

See [gist](https://gist.github.com/mgimenez/ae1cde0b637e844da885cb093a916126) for source.

Author: [@mgimenez](https://github.com/mgimenez/)

---

## Intika Theme

![img](https://github.com/Intika-Linux-Apps/Oh-My-Zsh-Intika/raw/master/capture.png)

See [repo](https://github.com/Intika-Linux-Apps/Oh-My-Zsh-Intika/blob/master/themes/intika.zsh-theme) for source.

Author: [Intika](https://github.com/intika)

---

## Philthy Theme

![img](https://imgur.com/am1MIxH.gif)

See [repo](https://gist.github.com/philFernandez/56f8953722285834cc9000ffcfe103f4#file-philthy-zsh-theme) for source.

Author: [Phil Fernandez](https://github.com/philFernandez) (philFernandez)

---

## Minimal Improved theme

![Minimal Improved theme for ZSH](https://raw.githubusercontent.com/gdsrosa/minimal_improved/master/minimal_improved_theme.png)

See [repo](https://github.com/gdsrosa/minimal_improved)
Author: [@gdsrosa](https://github.com/gdsrosa)

---

### kmac theme

![kmac theme for ZSH](https://github.com/koreymacdougall/config_files/blob/master/deprecated_files/kmac-zsh-theme-ss.png)

Simple theme that cleanly shows:
username@host:pwd $

See [repository](https://github.com/koreymacdougall/config_files/blob/master/deprecated_files/kmac.oh-my-zsh-theme) for source.
Author: [@koreymacdougall](https://github.com/koreymacdougall)

---

### Fishy2

![fishy2 zsh](https://github.com/akinjide/fishy2/raw/master/images/Screen%20Shot%202017-04-20%20at%2010.46.49%20AM.png)

See [repository](https://github.com/akinjide/fishy2) for source.

Author: [@akinjide](https://github.com/akinjide)

---

### abaykan

![abaykan](https://abaykan.com/server/abaykan.zsh-theme~.png)<br>
See [repository](https://github.com/abaykan/Mine/blob/master/abaykan.zsh-theme) for source.

Author: [@abaykan](https://github.com/abaykan)

---

### Oxide

![oxide zsh](https://files.dikiaap.id/img/dotfiles/zsh.png)

See [repository](https://github.com/dikiaap/dotfiles) for source.

Author: [@dikiaap](https://github.com/dikiaap)

### Windows CMD

![windows cmd](https://raw.githubusercontent.com/juliavallina/windows-zsh-theme/master/screenshot.gif)

See [repository](https://github.com/juliavallina/windows-zsh-theme) for source.

Author: [@juliavallina](https://github.com/juliavallina)

### sobole

[![sobole](https://github.com/sobolevn/sobole-zsh-theme/blob/master/showcases/ls-colors.png?raw=true)](https://sobolevn.github.io/sobole-zsh-theme/)
Github: https://github.com/sobolevn/sobole-zsh-theme

author: [@sobolevn](https://github.com/sobolevn)

### xxf

![xxf](https://i.ibb.co/rtGyPRs/Wechat-IMG230.png)

* Show Current commit shorten hash and message
See [Gist](https://gist.github.com/xfanwu/18fd7c24360c68bab884) for source.

author: [@xfanwu](https://github.com/xfanwu)

### Random Emoji Theme

![emoji theme](https://camo.githubusercontent.com/cef821db4ca342faa6a721a408a111d7ad91bb60/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f662e636c2e6c792f6974656d732f30633057327930573138335332543042337a30612f53637265656e2532305265636f7264696e67253230323031352d30352d30352532306174253230313525334131392e676966)

See [Gist](https://gist.github.com/oshybystyi/2c30543cd48b2c9ecab0) for source.

author: [@audy](https://github.com/audy), maintainer: [@oshybystyi](https://github.com/oshybystyi)

### powerlevel9k

![powerlevel9k theme](https://camo.githubusercontent.com/80ec23fda88d2f445906a3502690f22827336736/687474703a2f2f692e696d6775722e636f6d2f777942565a51792e676966)
A Powerline theme for ZSH that was written from scratch to address some of the speed issues in other feature-heavy themes. It comes with a great default setup, but is also highly configurable and can be heavily customized with built-in options. It also offers a large array of useful segments that you can add to your prompt, covering everything from Ruby versions to your AWS instance.

See [Powerlevel10k Repository](https://github.com/bhilburn/powerlevel9k) for source & documentation.

author: [@bhilburn](https://github.com/bhilburn)

### powerlevel10k

![powerlevel10k theme](https://camo.githubusercontent.com/80ec23fda88d2f445906a3502690f22827336736/687474703a2f2f692e696d6775722e636f6d2f777942565a51792e676966)
[Powerlevel10k](../powerlevel10k.md) is a backward-compatible reimplementation of the popular Powerlevel9k theme (see above) with 10-100 times better performance. When given the same configuration options it will generate the same prompt.

Powerlevel10k comes with an interactive configuration wizard that offers a wide range of prompt styles.
![powerlevel10k styles](https://raw.githubusercontent.com/romkatv/powerlevel10k/master/powerlevel10k.png)

See [Powerlevel10k repository](https://github.com/romkatv/powerlevel10k) for documentation.

author: [@romkatv](https://github.com/romkatv)

### Bullet train

![powerlevel9k theme](https://camo.githubusercontent.com/c5b0c78df1c3ca27bb2c5577114a92018bbdbee0/687474703a2f2f7261772e6769746875622e636f6d2f6361696f676f6e64696d2f62756c6c65742d747261696e2d6f682d6d792d7a73682d7468656d652f6d61737465722f696d672f707265766965772e676966)

Bullet Train is a Oh My Zsh shell theme based on the Powerline Vim plugin. It aims for simplicity, showing information only when it's relevant.

It currently shows:

* Current Python virtualenv
* Current Ruby version and gemset, through RVM
* Current Node.js version, through NVM
* Git status
* Timestamp
* Current directory
* Background jobs
* Exit code of last command

See [Repo](https://github.com/caiogondim/bullet-train-oh-my-zsh-theme) for source

author: [@caiogondim](https://github.com/caiogondim)

### Cordial

[![cordial](https://raw.githubusercontent.com/stevelacy/cordial-zsh-theme/master/screenshot.png)](https://raw.githubusercontent.com/stevelacy/cordial-zsh-theme/master/screenshot.png)

See [repository](https://github.com/stevelacy/cordial-zsh-theme) for source.

Additional setup:

* Install [node.js](https://nodejs.org/) to parse `package.json` files

### Gitster

![gitster theme](https://recordit.co/1Y5XxMkXFl.gif)

When in a git repo, it shows the location from the git's root folder.
When not in a git repo, it shows from home, `~`.

See my dotfiles [repo](https://github.com/shashankmehta/dotfiles/blob/master/thesetup/zsh/.oh-my-zsh/custom/themes/gitster.zsh-theme) for source.

author: [shashankmehta](https://github.com/shashankmehta)/[@leostatic](https://twitter.com/@leostatic)

### Lambda-Gitster

![lambda-gitster theme](https://raw.githubusercontent.com/ergenekonyigit/lambda-gitster/master/demo.gif)

Fork of gitster theme

source: [lambda-gitster](https://github.com/ergenekonyigit/lambda-gitster)

author: [ergenekonyigit](https://github.com/ergenekonyigit)/[@ergenekonyigit](https://twitter.com/ergenekonyigit)

### Pi

![pi theme](https://raw.githubusercontent.com/tobyjamesthomas/pi/master/demo.gif)

Version of gitster and lambda-gitster.

See [repository](https://github.com/tobyjamesthomas/pi) for source.

author: [tobyjamesthomas](https://github.com/tobyjamesthomas)

### Elessar

![Elessar theme](https://github.com/fjpalacios/elessar-theme/raw/master/elessar.gif)

Based on Gitster theme with a few improvements.

See [repo](https://github.com/fjpalacios/elessar-theme) for source.

Author: [@fjpalacios](https://github.com/fjpalacios)

### Chi

![Chi theme](https://github.com/akinjide/chi/raw/master/images/Screen%20Shot%202015-07-03%20at%2001.13.41.png)
![Chi theme](https://github.com/akinjide/chi/raw/master/images/Screen%20Shot%202015-07-03%20at%2001.14.40.png)

It currently shows:

* Git status
* 🕕 Time
* `~/Desktop` Working directory
* > where you type your cmds
* `✹git:master` **color : Red** unstaged commit
* `git:master` **color: White** committed files
* `○` shows if current directory is a git folder || git branch

See [repository](https://github.com/akinjide/chi) for source.

Author: [@akinjide](https://github.com/akinjide)

### Haribo theme

![haribotheme](https://fooo.biz/images/haribo_omz_theme.png)

* Works with most console fonts
* simple git status
* timestamp

See [Repo](https://github.com/haribo/omz-haribo-theme) for source

### Schminitz theme

![schminitztheme](https://g.recordit.co/krsXnCfF0W.gif)

This theme allow to see if vim is running on background when using the ':sh' command.

See [Gist](https://gist.github.com/schminitz/9931af23bbb59e772eec) for source.

author: [Schminitz](https://github.com/schminitz)/[@Schminitz](https://twitter.com/Schminitz)

### Odin theme

![odin](https://github.com/tylerreckart/odin/raw/master/images/preview.gif)

* Git focused development.
* A clean and distraction free programming environment.
* Know the status of your repository throughout the development process
* tmux and git configuration files included with the theme
See [odin](https://github.com/tylerreckart/odin) for source.

author: [@tylerreckart](https://github.com/tylerreckart)

### HYPERZSH theme

![hyperzsh](https://raw.githubusercontent.com/tylerreckart/hyperzsh/master/screenshots/demo.gif)

* Git status
* Timestamp
* Current directory
* Background jobs
* Exit code of last command

See [hyperzsh](https://github.com/tylerreckart/hyperzsh) for source.

author: [@tylerreckart](https://github.com/tylerreckart)

### Hyper Oh My Zsh

![Hyper Oh My Zsh](https://user-images.githubusercontent.com/1252570/43366555-1a7e5eb2-9383-11e8-89d5-98b255968bdb.png)

* Oh My Zsh theme based on hyper terminal default theme 😎

source: [here](https://github.com/willmendesneto/hyper-oh-my-zsh)
author: [@willmendesneto](https://github.com/willmendesneto)

### Lambda (Mod) theme

![Screenshot](https://raw.githubusercontent.com/halfo/lambda-mod-zsh-theme/master/screenshot.png)

* A simple yet elegant theme with git focused development.
See [lambda-mod](https://github.com/halfo/lambda-mod-zsh-theme/) for source.

author: [@halfo](https://github.com/halfo)

### Hedgehog theme

![hedgehog](https://i.imgur.com/GTbKcj5.gif)

* Simple, no-nonsense and clean, with support for git and return codes.

source: [here](https://gist.github.com/hedgehog1029/dfbb7e66511e2c399157)
author: [@hedgehog1029](https://github.com/hedgehog1029)

### Node theme

![node](https://raw.githubusercontent.com/skuridin/oh-my-zsh-node-theme/master/screenshot.png)

source: [here](https://github.com/skuridin/oh-my-zsh-node-theme)
author: [@skuridin](https://github.com/skuridin)

### classyTouch Theme

![classyTouch](https://raw.githubusercontent.com/pr0tocol/classyTouch_oh-my-zsh/master/classyTouch.png)

* A very minimal, clean theme with git support.

source: [here](https://github.com/yarisgutierrez/classyTouch_oh-my-zsh)
author: [@yarisgutierrez](https://github.com/yarisgutierrez)

### Spaceship

![Spaceship](https://user-images.githubusercontent.com/10276208/36086434-5de52ace-0ff2-11e8-8299-c67f9ab4e9bd.gif)

Spaceship is a minimalistic, powerful and extremely customizable Zsh prompt. It combines everything you may need for convenient work, without unnecessary complications, like a real spaceship.

Currently it shows:

* Clever hostname and username displaying.
* Prompt character turns red if the last command exits with non-zero code.
* Current Git branch and rich repo status:
  * `?` — untracked changes;
  * `+` — uncommitted changes in the index;
  * `!` — unstaged changes;
  * `»` — renamed files;
  * `✘` — deleted files;
  * `$` — stashed changes;
  * `=` — unmerged changes;
  * `⇡` — ahead of remote branch;
  * `⇣` — behind of remote branch;
  * `⇕` — diverged chages.
* Current Mercurial branch and rich repo status:
  * `?` — untracked changes;
  * `+` — uncommitted changes in the index;
  * `!` — unstaged changes;
  * `✘` — deleted files;
* Indicator for jobs in the background (`✦`).
* Current Node.js version, through nvm/nodenv/n (`⬢`).
* Current Ruby version, through rvm/rbenv/chruby (`💎`).
* Current Elixir version, through kiex/exenv/elixir (`💧`).
* Current Swift version, through swiftenv (`🐦`).
* Current Xcode version, through xenv (`🛠`).
* Current Go version (`🐹`).
* Current PHP version (`🐘`).
* Current Rust version (`𝗥`).
* Current version of Haskell Tool Stack (`λ`).
* Current Julia version (`ஃ`).
* Current Docker version and connected machine (`🐳`).
* Current Amazon Web Services (AWS) profile (`☁️`) ([Using named profiles](https://docs.aws.amazon.com/cli/latest/userguide/cli-multiple-profiles.html)).
* Current Python virtualenv.
* Current Conda virtualenv (`🅒`).
* Current Python pyenv (`🐍`).
* Current .NET SDK version, through dotnet-cli (`.NET`).
* Current Ember.js version, through ember-cli (`🐹`).
* Current Kubectl context (`☸️`).
* Package version, if there's is a package in the current directory (`📦`).
* Current battery level and status:
  * `⇡` - charging;
  * `⇣` - discharging;
  * `•` - fully charged.
* Current Vi-mode mode (with handy aliases for temporarily enabling).
* Optional exit-code of the last command.
* Optional time stamps 12/24hr in format.
* Execution time of the last command if it exceeds the set threshold.

source: [spaceship-prompt/spaceship-prompt](https://github.com/spaceship-prompt/spaceship-prompt)  
docs: [spaceship-prompt.sh](https://spaceship-prompt.sh)  
author: [@denysdovhan](https://twitter.com/denysdovhan)

### Zeta Theme

![zeta theme](https://user-images.githubusercontent.com/6789491/57182938-68197180-6ed8-11e9-9171-74b4618be62f.jpg)

Currently it shows:

* User name
* Machine name
* Current working directory
* Git branch
* Git status
    * `✔` —— Clean branch
    * `✘` —— Dirty branch
    * `+` —— Added files
    * `-` —— Deleted files
    * `*` —— Modified files
    * `>` —— Renamed files
    * `=` —— Unmerged changes
    * `?` —— Untracked changes
* Prompt indicator turns red if the last run fails

source: [here](https://github.com/skylerlee/zeta-zsh-theme)

author: [@skylerlee](https://github.com/skylerlee)

### AgnosterZak

![AgnosterZak theme](https://raw.githubusercontent.com/zakaziko99/agnosterzak-ohmyzsh-theme/master/images/agnosterzak-01.png)

AgnosterZak is a Oh My Zsh shell theme based on the Powerline Vim plugin & Agnoster Theme.

It currently shows:

* Battery Life (in case of the laptop is not charging)
* Current Date & Time
* Current directory
* Git status
* User & Host status

See [Repo](https://github.com/zakaziko99/agnosterzak-ohmyzsh-theme) for source

author: [@zakaziko99](https://github.com/zakaziko99)

### Nodeys

![Nodeys theme](https://raw.githubusercontent.com/marszall87/nodeys-zsh-theme/master/screenshot.png)

Nodeys is a theme based on fantastic ys theme, with added NodeJS version (from NVM plugin).

source: [Repo](https://github.com/marszall87/nodeys-zsh-theme) for source

author: [@marszall87](https://github.com/marszall87)

### Ciacho

![Ciacho theme](https://dl.dropboxusercontent.com/u/6741388/ciacho-zsh-theme.png)

Ciacho is theme based on agnoster.

See [Repo](https://github.com/Ciacho/ciacho-ohmyzsh-theme) for source.

author: [@Ciacho](https://github.com/Ciacho/)

### igorsilva

![igorsilva theme](https://raw.githubusercontent.com/igor9silva/zsh-theme/master/igorsilva.gif)

#### What it shows

* The current folder
* A customizable delimiter
* The current branch
* The current branch state (shows `*` if has uncommited changes)

See [Repo](https://github.com/igor9silva/zsh-theme) for source.

author: [@igor9silva](https://github.com/igor9silva/)

### nt9

![nt9 theme](https://raw.githubusercontent.com/lenguyenthanh/nt9-oh-my-zsh-theme/master/nt9.png)

A clean, distraction free and git focused development theme.

#### It currently shows:

* Show the location from git's root folder (when in a git repo) or show from home `~`
* Show current sha()
* Show current branch name
* Show current branch state (dirty, add, remove, delete...)
* Show time from last commit

See [Repo](https://github.com/lenguyenthanh/nt9-oh-my-zsh-theme) for source.

author: [@lenguyenthanh](https://github.com/lenguyenthanh)

### jovial

![jovial theme](https://github.com/zthxxx/jovial/raw/master/docs/jovial-preview.png)

pretty face, feel more jovial with this theme.

It currently shows:

* Show Host and User
* Show current path
* Show development environment segment
* Show git branch, git actions
* Show python venv
* Show time at the line end
* Show exit code at the previous line end

See [Repo](https://github.com/zthxxx/jovial) for source.

author: [@zthxxx](https://github.com/zthxxx)

### geometry

![geometry](https://raw.githubusercontent.com/frmendes/geometry/master/screenshots/geometry.png)

geometry is a minimalistic, fully customizable zsh prompt theme.

#### What it does:

* work asynchronously to speed up the prompt
* display current git branch
* display git state of the repo and time since last commit
* tell you whether you need to pull, push or if you're mid-rebase
* display the number of conflicting files and total number of conflicts
* display the running time of long running commands
* optionally display random colors based on your hostname
* give you a custom, colorizable prompt symbol
* change the prompt symbol color depending on the last command exit status
* show virtualenv and docker machine data
* set the terminal title to current command and directory
* fully customizable, allowing you to change anything through environment variables
* make you the coolest hacker in the whole Starbucks

See [repo](https://github.com/frmendes/geometry) for source. We welcome any contributions!

author: [@frmendes](https://github.com/frmendes)

### avit-da2k

![avit-da2k](https://raw.githubusercontent.com/fdaciuk/avit-da2k/master/dots.png)

A theme based on Avit, with small changes.

See [repo](https://github.com/fdaciuk/avit-da2k) for source.

author: [@fdaciuk](https://github.com/fdaciuk)

### kimwz

![kimwz](https://raw.githubusercontent.com/kimwz/kimwz-oh-my-zsh-theme/master/theme.jpg)

A minimal theme

See [repo](https://github.com/kimwz/kimwz-oh-my-zsh-theme) for source.

author: [@kimwz](https://github.com/kimwz)

### hub

![hub animated preview](https://gist.githubusercontent.com/hub23/c226b1c77446e099f7684b0d21c6b22a/raw/e4260d7135ef5ebfa26cdb084e43f3f03f86346a/zsh-preview.gif)

Simple and clean, visualizing return code.

See [gist](https://gist.github.com/hub23/c226b1c77446e099f7684b0d21c6b22a) for source.

author: [@hub23](https://github.com/hub23)

### Punctual

![Screenshot of Punctual in action](https://raw.githubusercontent.com/dannynimmo/punctual-zsh-theme/master/screenshot.png)

A simple, informative prompt built with Solarized colours in mind.

#### Features

* Customisable colours & output
* Git branch & status display
* Username turns red when root
* Prompt turns red if the last command finishes with non-zero exit code

See [repo](https://github.com/dannynimmo/punctual-zsh-theme) for installation.

By [Danny](https://github.com/dannynimmo).

### Staples

![Screenshot of Staples](https://github.com/dersam/staples/blob/master/sample.png?raw=true)

A modified version of the Bureau theme with context-sensitive tags, ssh status, and last exit code coloring.

See [repo](https://github.com/dersam/staples) for source.

Author: [@dersam](https://github.com/dersam)

### Bunnyruni

![Screenshot of Bunnyruni](https://raw.githubusercontent.com/jopcode/oh-my-zsh-bunnyruni-theme/master/bunnyruni.gif)

Simple, clean, and beautiful theme inspired in my fovorite themes, functions and colors.

See [repo](https://github.com/jopcode/oh-my-zsh-bunnyruni-theme) for source.

Author: [@jopcode](https://github.com/jopcode)

### traditional-plus

![screenshot](https://raw.githubusercontent.com/xfxf/zsh-theme-traditional-plus/master/screenshot.png)

Single-line boring/traditional prompt without distracting colours, providing extra information (currently git branch/status).

See [repo](https://github.com/xfxf/zsh-theme-traditional-plus) for source.
Author: [@xfxf](https://github.com/xfxf)

### oh-wonder

![screenshot](https://cloud.githubusercontent.com/assets/6545467/19431231/3c2bfa60-9475-11e6-98f7-312c749186cf.png)

Just another funky theme.

See [repo](https://gist.github.com/kaushik94/a54e128869c0c82bdbed31d56c710daa) for source.
Author: [@kaushik94](https://gist.github.com/kaushik94)

### rafiki-zsh

![screenshot](https://www.dropbox.com/s/u08c2zofducjvh9/rafiki-zsh-2.png?raw=1)

A zsh friend to watch over you.

See [repo](https://github.com/akabiru/rafiki-zsh) for source and instructions.
Author: [@akabiru](https://github.com/akabiru)

### λ Pure

![lambda-pure theme](https://raw.githubusercontent.com/marszall87/lambda-pure/master/screenshot.png)

A minimal zsh theme, based on Pure, with added NodeJS version (async!)

source: [Repo](https://github.com/marszall87/lambda-pure) for source

author: [@marszall87](https://github.com/marszall87)

### Imperator / Imperator Root

![imperator theme](https://raw.githubusercontent.com/LinuxGogley/Linux-Mods/master/Shell-Themes/Screenshot_2016-11-28_17-48-18.png)

An adaptation of the mortalscumbag theme.  Its modification no longer has the hostname next to the username on the prompt and has a better differentiation of colors by highlighting the user, working directory, and shell sign.  The theme also keeps the error number within brackets, as well as a running header stating whether the user is under an ssh connection.

source: [Repo](https://github.com/LinuxGogley/Linux-Mods/tree/master/Shell-Themes) for source

author: [@LinuxGogley](https://github.com/LinuxGogley)

### Oh-My-VIA

![oh-my-via theme](https://user-images.githubusercontent.com/19719047/85171739-db627c00-b26f-11ea-94ef-8f1f87929c47.png "Oh-My-VIA theme preview")

A theme for ZSH that is heavily inspired by the historical theme used on [VIA Centrale Réseaux](https://via.l4th.fr/) servers. It is designed to be as simple as possible, but still complete enough to be used on production servers and highly configurable to suit any of your desire.

See [Repo](https://github.com/badouralix/oh-my-via) for source & documentation.

author: [@badouralix](https://github.com/badouralix)

### alien

[![asciicast](https://asciinema.org/a/154047.png)](https://asciinema.org/a/154047)

Themes:
![blue](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/blue.png)
![green](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/green.png)
![red](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/red.png)
![soft](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/soft.png)

#### Features

* Time
* Battery percentage (with charging direction, - discharging, + charging, ● full-charge)
* Username
* Working directory
* Version control - branch, commit hash, dirty status, ahead/behind status
* Supports both mac and linux
* Asynchronously update prompt

See [Repo](https://github.com/eendroroy/alien) for source & documentation.

author: [@eendroroy](https://github.com/eendroroy)

### alien-minimal

[![asciicast](https://asciinema.org/a/264037.svg)](https://asciinema.org/a/264037)

#### Features

* Working directory
* Previous command exit status
* Version control - branch, commit hash, dirty status, ahead/behind status
* Supports both mac and linux
* Asynchronously update prompt
* Lots of configuration options
* **AND MANY MORE**

See [Repo](https://github.com/eendroroy/alien-minimal) for source & documentation.

author: [@eendroroy](https://github.com/eendroroy)

### Imp

![Screenshot of Imp](https://raw.githubusercontent.com/igormp/Imp/master/imp.png)

Simple theme based on [Zork](https://github.com/Bash-it/bash-it/wiki/Themes#zork).

See [repo](https://github.com/igormp/Imp) for source and install instructions.

Author: [@igormp](https://github.com/igormp)

### Omega

![Screenshot of Omega Minimal](https://raw.githubusercontent.com/Section214/zsh-omega/master/screenshots/minimal.png)

A clean, minimal theme.

See [repo](https://github.com/Section214/zsh-omega) for source and install instructions.

Author: [@igormp](https://github.com/igormp)

### Docker-ZSH

This theme is pretty much based on the 'bureau' theme. It has been extended by a `DOCKER_HOST` live view,
so that in every terminal session you see immediately which docker host is configured and where the local
docker commands are forwarded to.
If the `DOCKER_HOST` variable is not set in the terminal session, it's showing a green `local` text what can b
interpreted as a personal local test environment. If a remote host is defined it will show the address in `red`.

![Screenshot of Docker-zsh-theme](https://github.com/dpdornseifer/docker-zsh-theme/blob/master/sample.png)

See [repo](https://github.com/dpdornseifer/docker-zsh-theme) for source and install instructions.

Author: [@dpdornseifer](https://github.com/dpdornseifer)

### Vero

A theme designed for simplicity, neatness and availability of information. Vero offers:

* Timestamp
* Current Node.js version
* Current Git branch and status
* SSH indicator
* A fancy lambda symbol

![Screenshot of Vero](https://gitlab.com/thornjad/vero/-/raw/main/img/preview.png)

See [repo](https://gitlab.com/thornjad/vero) for source and documentation

Author: [@thornjad](https://github.com/thornjad)

### theta

[![asciicast](https://asciinema.org/a/121490.png)](https://asciinema.org/a/121490)

#### Features

* Working directory
* Version control - branch, commit hash, dirty status, ahead/behind status
* java, python, ruby. node versions
* Supports both mac and linux
* Asynchronously update prompt

See [Repo](https://github.com/eendroroy/theta) for source & documentation.

author: [@eendroroy](https://github.com/eendroroy)

### enlightenment

![enlightenment](https://w33tmaricich.com/images/enlightenment.png)

#### Features

* Current working directory.
* Clojure, python, and node version numbers, only when you need them.
* Number of seconds the previous command took to run.
* Git branch, dirty & clean.
* Color visuals for vi-mode.
* Clojure, python, and node version numbers, only when you need them.

See [repository](https://github.com/w33tmaricich/enlightenment) for source & documentation.

Author: [@w33tmaricich](https://w33tmaricich.com)

### iGeek

![iGeek](https://camo.githubusercontent.com/db9d61987431bc10c3b410e6b3bcf103240fd866/687474703a2f2f692e696d6775722e636f6d2f614154384242432e706e67)

See [repository](https://github.com/Saleh7/igeek-zsh-theme) for source.

### ASCIIGit

ASCII-only ZSH prompt theme (using Oh My Zsh) for git users who are not fan of fancy glyphs.

<img src="https://github.com/cemsbr/asciigit/blob/screenshot/screenshot.png?raw=true" width="606" height="468" alt="screenshot">

Features:

* Works well in terminal or console. No need to change your font!
* Git info:
  * Remote url, e.g. github.com/cemsbr/asciigit;
  * Relative path from git root dir;
  * Branch name;
  * Status (diverged, added, untracked, etc...).
* Colors known to work well with solarized light (probably with other schemes, too).

See [repository](https://github.com/cemsbr/asciigit) for source and readme.

Author: [@cemsbr](https://github.com/cemsbr)

### dpoggi-newline-timestamp

Timestamp and new line based on [dpoggi](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes#dpoggi) theme.

<img width="651" alt="2017-09-08 18 03 32" src="https://user-images.githubusercontent.com/1831308/30204562-dd033128-94c0-11e7-944c-19d7b0c18196.png">

Features:

* Timestamp
* New line for command

See [repository](https://github.com/channprj/dotfiles-macOS) for [source](https://github.com/channprj/dotfiles-macOS/blob/master/sh/zsh/custom-zsh-theme/dpoggi-timestamp.zsh-theme).

Author: [@channprj](https://github.com/channprj)

### nothing

![nothing](https://raw.githubusercontent.com/eendroroy/nothing/master/nothing.png)

#### Features

* Current sessions history count
* Exit code in right prompt on error

See [Repo](https://github.com/eendroroy/nothing) for source & documentation.

author: [@eendroroy](https://github.com/eendroroy)

### kinda-fishy

A theme based on [fishy](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes#fishy) with two differences:

* The full path is shown instead of abbreviated directory names.
* ```$USER@$HOST``` is not shown for the local machine, only for SSH sessions and
 inside docker containers (in that case it is ```$USER@docker```)

![Screenshot of kinda fishy](https://raw.githubusercontent.com/folixg/kinda-fishy-theme/master/screenshot.png)

See [repo](https://github.com/folixg/kinda-fishy-theme) for source

Author: [@folixg](https://github.com/folixg)

### blokkzh

Based on the built-in gnzh theme with added current Python virtualenv display.

![Screenshot of blokkzh](https://raw.githubusercontent.com/KorvinSilver/blokkzh/master/preview.png)

See [repo](https://github.com/KorvinSilver/blokkzh) for source.

Author: [@KorvinSilver](https://github.com/KorvinSilver)

### bender

Fancy two-line prompt with git integration.

Repo: https://github.com/specious/bender

![bender-zsh-theme](https://raw.githubusercontent.com/specious/bender/master/screenshot.png)

### agkozak

Uses three asynchronous methods to keep the ZSH prompt swift while displaying the Git status and indicators of SSH connection, exit codes, and `vi` mode, along with an abbreviated, `PROMPT_DIRTRIM`-style path. Very customizable. Asynchronous even on Cygwin and MSYS2.

![agkozak](https://raw.githubusercontent.com/agkozak/agkozak-zsh-prompt/master/img/demo.gif)

Repo: [https://github.com/agkozak/agkozak-zsh-prompt](https://github.com/agkozak/agkozak-zsh-prompt)

Author: [@agkozak](https://github.com/agkozak)

### rainbow-theme

![rainbow-theme](https://github.com/nivaca/rainbow-theme/blob/master/screenshot.png)

Repo: [https://github.com/nivaca/rainbow-theme](https://github.com/nivaca/rainbow-theme)

Author: [@nivaca](https://github.com/nivaca)

---

### Zeroastro Theme

![Zeroastro ZSH Theme](https://github.com/zeroastro/zeroastro-zsh-theme/raw/master/zeroastro-zsh-theme.png)

Simple, minimalistic theme for Oh My ZSH.

Repo: [https://github.com/zeroastro/zeroastro-zsh-theme](https://github.com/zeroastro/zeroastro-zsh-theme)

Author: [@zeroastro](https://github.com/zeroastro)

---

### Kayid Theme

![Kayid Theme for ZSH](https://raw.githubusercontent.com/AmrMKayid/KayidmacOS/master/Kayid-Theme.png)

See [repo](https://github.com/AmrMKayid/KayidmacOS/blob/master/kayid.zsh-theme)
Author: [@AmrMKayid](https://github.com/AmrMKayid)

---

### Shayan ZSH Theme

![Shayan ZSH Theme](https://raw.githubusercontent.com/shayanh/shayan-zsh-theme/master/shayan-zsh-theme.png)

Simple.

Repo: [https://github.com/shayanh/shayan-zsh-theme](https://github.com/shayanh/shayan-zsh-theme)

Author: [@shayanh](https://github.com/shayanh)

---

### FunkyBerlin Theme

![FunkyBerlin](https://raw.githubusercontent.com/Ottootto2010/funkyberlin-zsh-theme/master/showcase.png)

A colorfull two-line theme with support for GIT and SVN.

Repo: [https://github.com/Ottootto2010/funkyberlin-zsh-theme](https://github.com/Ottootto2010/funkyberlin-zsh-theme)

Author: [@Ottootto2010](https://github.com/Ottootto2010/funkyberlin-zsh-theme)

---

### RobbyRussell-WIP Theme

![img](https://raw.githubusercontent.com/ecbrodie/robbyrussell-WIP-theme/master/images/screenshot.png)

The same RobbyRussell theme that everyone loves, decorated with a `WIP!!` message when the latest commit of your git repo is a WIP commit.

Repo: https://github.com/ecbrodie/robbyrussell-WIP-theme

Author: [@ecbrodie](https://github.com/ecbrodie)

---

### McQuen Theme

![McQuen](https://user-images.githubusercontent.com/772937/54210241-5d27ff00-449c-11e9-81b3-64efe0a13f6c.png)

A minimalist two line theme with Git support and a Lambda (λ) shell.

Repo: [https://gist.github.com/ryanpcmcquen/150cf9a66bca2463e5660cafed3e1000](https://gist.github.com/ryanpcmcquen/150cf9a66bca2463e5660cafed3e1000)

Author: [@ryanpcmcquen](https://github.com/ryanpcmcquen)

---

### sm

![sm-theme](https://raw.githubusercontent.com/blyndusk/sm-theme/master/docs/sm-theme.gif)

⛓ a **Simplistic** & **Minimalist** theme for **`ZSH`** prompts.

source: [Repo](https://github.com/blyndusk/sm-theme) for source.

author: [@blyndusk](https://github.com/blyndusk)

---

### minimal2

![minimal2](https://github.com/girishrau/oh-my-zsh-customizations/blob/master/images/minimal2.jpg)

A minimalist two line theme with Git support.

Repo: [https://github.com/girishrau/oh-my-zsh-customizations](https://github.com/girishrau/oh-my-zsh-customizations)

Author: [@girishrau](https://github.com/girishrau)

---

### drofloh

![screenshot](https://raw.githubusercontent.com/drofloh/oh-my-zsh-custom/master/screenshot.png)

Custom theme...

Source: [drofloh.zsh-theme](https://github.com/drofloh/oh-my-zsh-custom)

Author: [@drofloh](https://github.com/drofloh)

---

### lambda-v

![screenshot](https://raw.githubusercontent.com/vkaracic/lambdav-zsh-theme/master/screenshot.png)

Two-line prompt that includes system clock timestamps, username, current working directory, git branch, git prompt info.

Source: [lambda-v.zsh-theme](https://github.com/vkaracic/lambdav-zsh-theme)

Author: [@vkaracic](https://github.com/vkaracic)

---

### Halil

![Halil Theme](https://raw.githubusercontent.com/5m0k3r/zsh-themes/master/zsh-theme-halil-thumb.gif)

Simple prompt with system clock, current working directory, git prompt info and nice user prompt.

Source: [halil.zsh-theme](https://github.com/5m0k3r/zsh-themes)

Author:  [@5m0k3r](https://github.com/5m0k3r)

### Maza

![Maza Theme](https://raw.githubusercontent.com/eamazaj/maza-theme/master/video.gif)

Simple is better

Source: [maza.zsh-theme](https://github.com/eamazaj/maza-theme)

Author:  [@eamazaj](https://github.com/eamazaj)

### Chill

![Chill Theme](https://raw.githubusercontent.com/PsychoPatate/chill.zsh-theme/master/chill.png)

Clean and simple look with return status, git status and full path.

Source: [chill.zsh-theme](https://github.com/PsychoPatate/chill.zsh-theme)

Author:  [@PsychoPatate](https://github.com/PsychoPatate)

### Solus

![Solus Theme](https://gist.githubusercontent.com/cloudnull/4cc7890acaae6cb809e811e09e9eaade/raw/f62c35e3f1a383dbd281fbdaaede00069582141d/solus-oh-my-zsh-theme.png)

Simple theme was based on Bira, and influenced by the default Bash PS1 from Solus. The theme returns exit, git, rvm, and venv status as well as the full path.

Source: [solus.zsh-theme](https://gist.github.com/cloudnull/4cc7890acaae6cb809e811e09e9eaade#file-solus-zsh-theme)

Author:  [@cloudnull](https://github.com/cloudnull)

### gitstatus

[Official repository](https://github.com/kimyvgy/gitstatus-zsh-theme)

[![gitstatus](https://raw.githubusercontent.com/kimyvgy/gitstatus-zsh-theme/master/gitstatus.png)](https://cloud.githubusercontent.com/assets/2618447/6316736/51c6a6c8-ba00-11e4-8b5f-b45795d98907.png)

### Antsy

![Antsy](https://raw.githubusercontent.com/jeffmhubbard/antsy-zsh-theme/assets/demo.png)

Multiline Oh My Zsh theme with git info, virtualenv, vi-mode indicator, current history, jobs count, and exit status.

Source: [antsy.zsh-theme](https://github.com/jeffmhubbard/antsy-zsh-theme)

Author:  [@jeffmhubbard](https://github.com/jeffmhubbard)

### thm

![thm](https://raw.githubusercontent.com/sudo-HackerMan/thm-zshtheme/master/screenshot.png)

Modified 'The Poncho' theme.

Source: [thm.zsh-theme](https://github.com/sudo-HackerMan/thm-zshtheme)

Author: [@sudo-HackerMan](https://github.com/sudo-HackerMan)

Original: [@RainyDayMedia](https://github.com/RainyDayMedia/oh-my-zsh-poncho)

### None Theme

![none-theme](https://user-images.githubusercontent.com/43632885/83956911-a1c55600-a817-11ea-97d1-65c32238fb23.png)

Absolutely no prompt. Useful if you want a super minimal prompt (but still want Oh My Zsh for other plugins), or if you're replacing your prompt (i.e. with [Starship](https://starship.rs))

Source: File `none.zsh-theme` containing only the line `PROMPT=""`.

Author: [@catleeball](https://github.com/catleeball)

### fishbone++

#### Features:

* emoji git status :)
* fault return indicator
* various customization
  * prompt layout
  * prompt symbol
  * time
  * new line after every command

![fishbone++](https://github.com/EYH0602/Fishbonepp/blob/master/pics/defaultlook.png)  
Source: [fishbone++](https://github.com/EYH0602/Fishbonepp)  
Author: [@EYH0602](https://github.com/EYH0602)  

### Ohio2's themes!

#### Features:

* Simple
* One based on dallas
* a whole collection.
* Easy to customize
* Time marker (ohio2, not ybl)
* Git marker.

Themes:[Ohio2's themes repo](https://github.com/Ohio2/dotfiles-ohio2/tree/master/.oh-my-zsh/themes)
![zsh-ohio2](https://i.imgur.com/tKc6B1P.png)

---

<br/>
<h3 align="center"><a href="https://github.com/ice-bear-forever/bubblegum-zsh">bubblegum</a></h3>
<p align="center">a deliciously minimalist light pink theme</p>
<br/>
<a href="https://github.com/ice-bear-forever/bubblegum-zsh"><p align="center">
  <img src="https://github.com/ice-bear-forever/bubblegum-zsh/blob/main/screenshot.png"/>
</p></a>

#### features:

* a triangular glyph and your working directory, nothing more
* a [matching theme](https://github.com/ice-bear-forever/hyper-bubblegum) for [Hyper](https://hyper.is) terminal

repository: [bubblegum-zsh](https://github.com/ice-bear-forever/bubblegum-zsh/)

author: [@ice-bear-forever](https://github.com/ice-bear-forever/)

---

<br/>
<h3 align="center"><a href="https://github.com/tigerjz32/kube-zsh-theme">kube</a></h3>
<p align="center">a colorful and informative theme</p>
<br/>
<a href="https://github.com/tigerjz32/kube-zsh-theme"><p align="center">
  <img src="https://github.com/tigerjz32/kube-zsh-theme/blob/main/assets/image1.jpg"/>
</p></a>

#### features:

* shows the current time

* shows current kubectl context
* shows current dir
* shows current Git branch
* shows an arrow to differentiate input vs prompt
* uses different colors for readability

repository: [kube-zsh-theme](https://github.com/tigerjz32/kube-zsh-theme/)

author: [@tigerjz32](https://github.com/tigerjz32)

### shini

![shini](https://raw.github.com/bashelled/shini/master/screenshot.png)

A simple zsh theme. With your average time, exit status, user@host, directory and git branch, you can just install and relax.

See [repository](https://github.com/bashelled/shini) for installation.

Author: [@bashelled](https://github.com/bashelled)

### ivabus

![ivabus](https://github.com/ivabus/ivabus-zsh-theme/blob/main/screenshot.png)

repository: [ivabus-zsh-theme](https://github.com/ivabus/ivabus-zsh-theme)

author: [@ivabus](https://github.com/ivabus)


## See also

- [Oh My Zsh Github](https://github.com/ohmyzsh/ohmyzsh)
- [Powerlevel10k Zsh theme](../powerlevel10k.md)
- [Zsh](../zsh.md)
