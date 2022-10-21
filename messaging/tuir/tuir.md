---
tags:
    - python
    - reddit
    - commandline
    - command-line
    - terminal
categories:
    - tui
    - python
---

# Terminal UI for Reddit (TUIR)

A text-based interface (TUI) to view and interact with Reddit from your terminal.

TUIR is a fork of rtv, which was maintained by Michael Lazar in [this repository](https://github.com/michael-lazar/rtv) until Jun 3, 2019.

![title](https://raw.githubusercontent.com/proycon/tuir/master/resources/title_image.png)

## Table of Contents

1. [Demo](#demo)  
1. [Installation](#installation)  
1. [Usage](#usage)  
1. [Settings](#settings)
1. [Themes](#themes)
1. [FAQ](#faq)  
1. [Contributing](#contributing)  
1. [License](#license)  

## Demo

![demo image](https://raw.githubusercontent.com/proycon/tuir/master/resources/demo.gif)

## Installation

### PyPI package

TUIR is available on [PyPI](https://pypi.python.org/pypi/tuir/) and can be installed with pip:

```bash
pip install tuir
```

#### Migration from RTV

If you are migrating from RTV to TUIR, you can simply rename your old config directory/config file:

```bash
mv ~/.config/rtv ~/.config/tuir
mv ~/.config/tuir/rtv.cfg ~/.config/tuir/tuir.cfg
```

Please take care to use the new API keys for Imgur and Reddit. To replace with sed:

```bash
sed -i 's/E2oEtRQfdfAfNQ/zjyhNI7tK8ivzQ/; s/93396265f59dec9/b33d69ac8931734/' ~/.config/tuir/tuir.cfg
```

### Distro packages

See [Repology](https://repology.org/metapackage/tuir/packages) for an up-to-date list of supported distro packages.

#### Arch

TUIR is available from the AUR with the package name `TUIR`.

### From source

```bash
git clone https://gitlab.com/ajak/tuir.git
cd tuir
python setup.py install
```

### Windows

TUIR is not supported on Windows, due to a lack of resources and interest. Sorry!

## Usage

To run the program, type:

```bash
tuir --help
```

### Controls

Move the cursor using either the arrow keys or *Vim* style movement:

- Press <kbd>▲</kbd> and <kbd>▼</kbd> to scroll through submissions
- Press <kbd>▶</kbd> to view the selected submission and <kbd>◀</kbd> to return
- Press <kbd>space-bar</kbd> to expand/collapse comments
- Press <kbd>u</kbd> to login (this requires a web browser for [OAuth](https://github.com/reddit-archive/reddit/wiki/oauth2))
- Press <kbd>?</kbd> to open the help screen

Press <kbd>/</kbd> to open the navigation prompt, where you can type things like:

- ``/front``
- ``/r/commandprompt+linuxmasterrace``
- ``/r/programming/controversial``
- ``/u/me``
- ``/u/multi-mod/m/art``
- ``/domain/github.com``

See [controls](controls.md) for the full list of commands.

## Settings

### Configuration File

Configuration files are stored in the ``{HOME}/.config/tuir/`` directory.

Check out [tuir.cfg](tuir.cfg) for the full list of configurable options. You can clone this file into your home directory by running:

```bash
tuir --copy-config
```

### Viewing Media Links

You can use [mailcap](https://en.wikipedia.org/wiki/Media_type#Mailcap) to configure how TUIR will open different types of links.

![mailcap](https://raw.githubusercontent.com/proycon/tuir/master/resources/mailcap.gif)

A mailcap file allows you to associate different MIME media types, like ``image/jpeg`` or ``video/mp4``, with shell commands. This feature is disabled by default because it takes a few extra steps to configure. To get started, copy the default mailcap template to your home directory.

```bash
tuir --copy-mailcap
```

This template contains examples for common MIME types that work with popular reddit websites like *imgur*, *youtube*, and *gfycat*. Open the mailcap template and follow the [instructions](mailcap.md) listed inside.

Once you've setup your mailcap file, enable it by launching tuir with the ``tuir --enable-media`` flag (or set it in your **tuir.cfg**)

### Environment Variables

The default programs that TUIR interacts with can be configured through environment variables:

| Variable | Description |
|----------|-------------|
| TUIR_EDITOR | A program used to compose text submissions and comments, e.g. **vim**, **emacs**, **gedit**.  *If not specified, will fallback to $VISUAL and $EDITOR in that order.* |
| TUIR_BROWSER | A program used to open links to external websites, e.g. **firefox**, **google-chrome**, **w3m**, **lynx**. *If not specified, will fallback to $BROWSER, or your system's default browser.* |
| TUIR_URLVIEWER | A tool used to extract hyperlinks from blocks of text, e.g. [urlview](https://github.com/sigpipe/urlview), [urlscan](https://github.com/firecat53/urlscan). *If not specified, will fallback to urlview if it is installed.* |

### Clipboard

TUIR supports copying submission links to the OS clipboard.  Data being copied is piped into a command specified by the configuration option `clipboard_cmd`. If this option is not set, the command will default to `pbcopy w` on Darwin systems (OSX), and `xclip -selection clipboard` on Linux.

## Themes

Themes can be used to customize the look and feel of TUIR

| Solarized Dark | Solarized Light |
|----------------|-----------------|
| ![theme](https://raw.githubusercontent.com/proycon/tuir/master/resources/theme_solarized_dark.png) | ![theme](https://raw.githubusercontent.com/proycon/tuir/master/resources/theme_solarized_light.png) |

| Papercolor | Molokai |
|------------|---------|
| ![theme](https://raw.githubusercontent.com/proycon/tuir/master/resources/theme_papercolor.png) | ![theme](https://raw.githubusercontent.com/proycon/tuir/master/resources/theme_molokai.png) |

You can list all installed themes with the ``--list-themes`` command, and select one with ``--theme``. You can save your choice permanently in your [tuir.cfg](tuir.cfg) file. You can also use the <kbd>F2</kbd> & <kbd>F3</kbd> keys inside of TUIR to cycle through all available themes.

For instructions on writing and installing your own themes, see [themes](themes.md).

## FAQ

<details>
 <summary>Why am I getting an error during installation/when launching tuir?</summary>
 
  > If your distro ships with an older version of python 2.7 or python-requests,
  > you may experience SSL errors or other package incompatibilities. The
  > easiest way to fix this is to install tuir using python 3. If you
  > don't already have pip3, see http://stackoverflow.com/a/6587528 for setup
  > instructions. Then do
  >
  > ```bash
  > $ sudo pip uninstall tuir
  > $ sudo pip3 install -U tuir
  > ```

</details>
<details>
  <summary>Why do I see garbled text like <em>M-b~@M-"</em> or <em>^@</em>?</summary>
 
  > This type of text usually shows up when python is unable to render
  > unicode properly.
  >    
  > 1. Try starting TUIR in ascii-only mode with ``tuir --ascii``
  > 2. Make sure that the terminal/font that you're using supports unicode
  > 3. Try [setting the LOCALE to utf-8](https://perlgeek.de/en/article/set-up-a-clean-utf8-environment)
  > 4. Your python may have been built against the wrong curses library,
  >    see [here](stackoverflow.com/questions/19373027) and
  >    [here](https://bugs.python.org/issue4787) for more information

</details>
<details>
 <summary>How do I run the code directly from the repository?</summary>
 
  > This project is structured to be run as a python *module*. This means that
  > you need to launch it using python's ``-m`` flag. See the example below, which
  > assumes that you have cloned the repository into the directory **~/tuir_project**.
  >
  > ```bash
  > $ cd ~/tuir_project
  > $ python3 -m tuir
  > ```

</details>

## Current development status

TUIR currently depends on Michael Lazar's (maintainer of RTV) fork of PRAW being packaged with the program. Michael's fork is a fork from PRAW version 3.6.1, which is [currently unsupported](https://github.com/praw-dev/praw/blob/master/SECURITY.md). Further, packaged dependencies aren't looked upon fondly by various distribution's packaging guidelines ([#11](https://gitlab.com/ajak/tuir/issues/11), [Gentoo Wiki - Why not bundle dependencies](https://wiki.gentoo.org/wiki/Why_not_bundle_dependencies)). Due to this, I'm working to update TUIR to a more recent PRAW version which isn't bundled.

There is significant API breakage from PRAW 3 to PRAW 6 (the [PRAW README](https://github.com/praw-dev/praw/) calls PRAW 4 a "complete rewrite"). As such, updating TUIR to use a PRAW multiple major versions newer is slow going. I am a relatively inexperienced developer and I have less time than I'd like to devote to software. This work is in branch `update_unbundle_praw` ([link](https://gitlab.com/ajak/tuir/-/commits/update_unbundle_praw)), so there may not be super recent commits in `master`, but that doesn't mean I'm neglecting TUIR. Unfortunately, this does mean I am not actively working on feature requests. They are always welcome of course, but it would be far simpler to add features after TUIR is converted to using PRAW 6 instead of adding them now and dealing with their breakage later.

Python 2 is also [dead](https://devguide.python.org/devcycle/#end-of-life-branches) as of 2020. PRAW 6 doesn't even support Python 2, so Python 2 support in TUIR is also being dropped. Given that PRAW3 is packaged with TUIR as a result of RTV doing the same, there is little sense in removing Python 2 support from the packaged version when there is already an updated version of PRAW available, so I will work to remove Python 2 support alongside my efforts to update TUIR for PRAW 6.

## Contributing

View a [list of authors and contributors](authors.md).

All feedback and suggestions are welcome, just post an issue!

Before writing any code, please read the [Contributor Guidelines](contributing.md).

## License
This project is distributed under the [MIT](license.md) license.

## See also

- [Asciiville](../../projects/Asciiville.md)
- [Python](../../linux/python.md)
- [Authors](authors.md)
- [Changelog](changelog.md)
- [Contributing](contributing.md)
- [Controls](controls.md)
- [License](license.md)
- [Mailcap](mailcap.md)
- [Themes](themes.md)
- [Tuir Configuration](tuir.cfg.md)
- [Irssi](../irssi.md)
- [Neomutt](../neomutt.md)
- [Newsboat](../newsboat.md)
