---
tags:
  - projects
  - magicmirror
  - commandline
---

> **"The cosmic operating system uses a command line interface. It runs on
> something like a teletype, with lots of noise and heat; punched-out bits
> flutter down into its hopper like drifting stars. The demiurge sits at his
> teletype, pounding out one command line after another, specifying the values
> of fundamental constants of physics:**
>
> `universe -G 6.672e-11 -e 1.602e-19 -h 6.626e-34 -protonmass 1.673e-27`
>
> **and when he’s finished typing out the command line, his right pinky hesitates
> above the enter key for an aeon or two, wondering what’s going to happen;
> then down it comes—and the whack you hear is another Big Bang."**
>
> ― Neal Stephenson, In the Beginning...Was the Command Line

# MirrorCommand
[MagicMirror](https://magicmirror.builders) is an open source modular
smart mirror platform (see https://magicmirror.builders/).
This repository maintains an extensive set of scripts to initialize,
configure, monitor, and manage a MagicMirror.

## Table of contents

1. [Overview](#overview)
1. [Compatibility](#compatibility)
1. [Installation](#installation)
    1. [MagicMirror Installation](#magicmirror-installation)
    1. [MirrorCommand Installation](#mirrorcommand-installation)
        1. [Pre Installation](#pre-installation)
        1. [Debian Package installation](#debian-package-installation)
        1. [RPM Package installation](#rpm-package-installation)
        1. [ALSA audio input and output devices configuration](#alsa-audio-input-and-output-devices-configuration)
    1. [Post installation configuration](#post-installation-configuration)
        1. [Add keys to mirrorkeys](#add-keys-to-mirrorkeys)
        1. [Configure mirror script](#configure-mirror-script)
        1. [Rerun initialization scripts](#rerun-initialization-scripts)
        1. [Image archive installation](#image-archive-installation)
1. [Custom Package Creation](#custom-package-creation)
1. [Removal](#removal)
1. [Supporting utilities and config files](#supporting-utilities-and-config-files)
1. [Remote access](#remote-access)
    1. [Remote execution of mirror commands](#remote-execution-of-mirror-commands)
    1. [Remote view of MagicMirror display](#remote-view-of-magicmirror-display)
    1. [MMM-Remote-Control integration](#mmm-remote-control-integration)
    1. [MMM-TelegramBot integration](#mmm-telegrambot-integration)
        1. [MMM-TelegramBot installation](#mmm-telegrambot-installation)
        1. [MMM-TelegramBot module config](#mmm-telegrambot-module-config)
        1. [MMM-TelegramCommands module](#mmm-telegramcommands-module)
        1. [Telegram usage](#telegram-usage)
1. [MMM-GoogleAssistant integration](#mmm-googleassistant-integration)
    1. [Google Cloud Platform API Keys](#google-cloud-platform-api-keys)
1. [MMM-Scenes integration](#mmm-scenes-integration)
1. [Usage](#usage)
    1. [Getting to the Command Line](#getting-to-the-command-line)
    1. [Switching screens](#switching-screens)
        1. [Using the mirror command to switch screens](#using-the-mirror-command-to-switch-screens)
        1. [Using voice commands to switch screens](#using-voice-commands-to-switch-screens)
1. [Documentation](#documentation)
1. [Motivation](#motivation)
    1. [Introduction to Using the Command Line](#introduction-to-using-the-command-line)
    1. [Why would I need or want command line control of MagicMirror](#why-would-i-need-or-want-command-line-control-of-magicmirror)
    1. [History](#history)
1. [Contents](#contents)
1. [Known Limitations](#known-limitations)
1. [Screenshots](#screenshots)
1. [License](#license)
1. [See also](#see-also)

## Overview

The Mirror Command Line project provides scripts to enable
command line control of the MagicMirror system over a local network.
The MirrorCommand Debian and RPM format package installation scripts perform
automatic installation and configuration of a MagicMirror including:

- Automated installation of the MagicMirror software if not already installed
- Automated configuration of the MagicMirror
- Automated installation and configuration of several MagicMirror modules
- PM2 process manager installation and configuration
- Semi-automated key management to enable a single source for adding, storing, and managing the several keys necessary to activate many MagicMirror modules
- Hundreds of MagicMirror configuration files preconfigured with layouts for both portrait and landscape mode displays and module activation

The `mirror` command can be installed on your MagicMirror to issue
MagicMirror commands. Currently the command line MagicMirror control scripts
include support for:

- Specifying the MagicMirror configuration file to activate
- Starting, stopping, and restarting the MagicMirror
- Display of various system info
    - Temperature
	- Memory
	- Disk
	- Usb
	- Network
	- Wireless
	- Screen
- List active/installed MagicMirror modules
- List available MagicMirror configuration files
- Rotate the MagicMirror screen
- Get or set the brightness level
- Control MagicMirror video playback
    - Start/Stop video play
	- Replay video
	- Play next video
	- Hide video playback module
	- Show video playback module
- Control the MagicMirror audio output volume level
- Get MagicMirror status
- Update the MagicMirror installation or update installed modules
- Auto generation of new MagicMirror configuration files
- Interactive mode via menu dialogs
    - Invoked with no arguments the mirror command displays a command menu.

## Compatibility
MirrorCommand has been successfully deployed and tested on a Raspberry Pi 4
and Raspberry Pi 400 running Raspbian Buster. It has also been deployed and
tested on Ubuntu Linux 20.04 and Fedora Linux 35 with generic x86_64 hardware.

It has been tested on systems with a mirror display and systems with a
standard computer monitor display. MirrorCommand version 2.7 and later
has been tested on systems with multiple monitors. Testing has been performed
on systems with a variety of screen resolutions and orientation including
1920x1080 portrait mode display, 2560x1440 landscape mode display, and
1920x1080 landscape mode display. Deployment of the MirrorCommand
MagicMirror configuration files on screens with display resolution differing
significantly from those tested may require changes to the module positions,
layout, and geometry.

MirrorCommand installation packages are available in both the Debian packaging
format and the RPM packaging format so the automated installation is available
for all systems that support Debian or RPM packaging formats.
That's most Linux environments.

## Installation

### MagicMirror Installation
MirrorCommand is intended for installation on a system running
[MagicMirror](https://magicmirror.builders). If MagicMirror is not
previously installed it can be installed following
[these instructions](https://docs.magicmirror.builders/getting-started/installation.html#manual-installation). Alternatively, the MirrorCommand Debian or RPM package
format installation will automatically install and configure MagicMirror if no
existing MagicMirror installation is detected. This automated installation
of MagicMirror includes installing and configuring PM2 for easy and powerful
process management of MagicMirror as well as the installation of several
MagicMirror 3rd party modules used by MirrorCommand.

**Note:** An actual mirror with display mounted on the rear is not necessary.
MagicMirror can be installed on a Raspberry Pi with a mirror display as intended or
it can be installed on a Debian based Linux system (e.g. Ubuntu Linux) or an RPM
based Linux system (e.g. Fedora Linux) with standard monitor and desktop environment.

MagicMirror requires Node version 12 or later.

MirrorCommand assumes that MagicMirror is installed in either
`/usr/local/MagicMirror` or a user's home directory.

To install MagicMirror simply install MirrorCommand using the Debian or RPM
package format available at the
[MirrorCommand Releases](https://gitlab.com/doctorfree/MirrorCommand/-/releases)
area of the Git repository.

If MagicMirror is not installed in either `/usr/local/MagicMirror` or a non-root
user's home directory, then the MirrorCommand installation will ask if you
wish to install MagicMirror and, if so, will install MagicMirror in `/usr/local`.
In addition to performing a MagicMirror installation and configuration, the
MirrorCommand installation will install and configure several MagicMirror
modules and PM2 process management.

Alternatively, MagicMirror can be installed manually following these steps:

- Change directory to either `/usr/local` or a non-root user's home directory
- From either `/usr/local` or a non-root user's home directory, execute the following commands:
    - Download and install the latest Node.js version
        - `curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -`
        - `sudo apt install -y nodejs`
    - Clone the repository and check out the master branch
        - `git clone https://github.com/MichMich/MagicMirror`
    - Enter the repository
        - `cd MagicMirror`
    - Install the application
        - `npm install`
    - Make a copy of the config sample file
        - `cp config/config.js.sample config/config.js`
    - Start the application
        - `npm run start`

To start the MagicMirror over SSH from a remote terminal, use the commands:

- `cd /path/to/MagicMirror`
- `DISPLAY=${DISPLAY:=:0} nohup npm start &`

To access the toolbar menu when in mirror mode, press the ALT key.

### MirrorCommand Installation

MirrorCommand v3.0 and later can be installed on Linux systems using
either the Debian packaging format or the Red Hat Package Manager (RPM).

#### Pre Installation

**XHOST:** The automated configuration requires access to some X11 graphical
utilities. Depending upon your system's X11 configuration, it may be necessary
to grant the *root* user access to the display. To do so, prior to installation
issue the command:

`xhost +si:localuser:root`

or grant everyone access with

`xhost +`

**ROON:** If you plan to install both the
[RoonCommandLine package](https://gitlab.com/doctorfree/RoonCommandLine)
and the
[MirrorCommand package](https://gitlab.com/doctorfree/MirrorCommand)
on the same system then in order to enable automatic configuration of
MirrorCommand's Roon configuration files, the RoonCommandLine
package must be installed before the MirrorCommand package.

After granting X11 access with `xhost` and optionally installing
RoonCommandLine, install MirrorCommand following either the
[Debian package installation guide](#debian-package-installation)
or [RPM package installation guide](#rpm-package-installation).

#### Debian Package installation

Many Linux distributions, most notably Ubuntu and its derivatives, use the
Debian packaging system.

To tell if a Linux system is Debian based it is usually sufficient to
check for the existence of the file `/etc/debian_version` and/or examine the
contents of the file `/etc/os-release`.

To install on a Debian based Linux system, download the latest Debian
format package from the
[MirrorCommand releases](https://gitlab.com/doctorfree/MirrorCommand/-/releases).

Install the MirrorCommand package by executing the command

```bash
sudo apt install ./MirrorCommand_<version>-<release>.deb
```
or
```console
sudo dpkg -i ./MirrorCommand_<version>-<release>.deb
```

#### RPM Package installation

Red Hat Linux, SUSE Linux, and their derivatives use the RPM packaging
format. RPM based Linux distributions include Fedora, AlmaLinux, CentOS,
openSUSE, OpenMandriva, Mandrake Linux, Red Hat Linux, and Oracle Linux.

To install on an RPM based Linux system, download the latest RPM format
package from the
[MirrorCommand releases](https://gitlab.com/doctorfree/MirrorCommand/-/releases).

Install the MirrorCommand package by executing the command

```bash
sudo yum localinstall ./MirrorCommand_<version>-<release>.rpm
```
or
```console
sudo rpm -i ./MirrorCommand_<version>-<release>.rpm
```

#### ALSA audio input and output devices configuration
The MirrorCommand installation attempts to detect and configure ALSA
audio input and output devices such as a microphone, webcam, or DAC.

The installation process will modify `/etc/asound.conf` if it detects
audio devices incorrectly configured. No changes are made to individual
users' `.asoundrc` in their home directories. If you wish to override the
settings configured by the `set_asound_conf` command, you can do so by
creating an `.asoundrc` file in your home directory and managing the ALSA
audio device settings there.

To reconfigure the `/etc/asound.conf` ALSA audio configuration file,
issue the command:

`sudo /usr/local/bin/set_asound_conf`

### Post installation configuration

The MirrorCommand installation process cannot automatically configure
your private keys which are used to access various services the MagicMirror
utilizes. For example, you may have private keys to access a weather service,
Telegram, Google services, or the MMM-Remote-Control module.

Before you can use the MirrorCommand utilites and config files you will
need to add any keys you wish to use to the appropriate config files and utilities.

#### Add keys to mirrorkeys

**Don't Panic!** The MirrorCommand package includes utilities to add and
remove private keys. To do so:

Edit the file `/usr/local/MirrorCommand/etc/mirrorkeys` adding the keys you have
previously generated/retrieved to each of the 'keys[FOO]' settings with corresponding
'dumb[FOO]' setting, leaving the 'dumb[FOO]' setting as-is

Add the keys you wish to set and leave those you do not wish to set empty

After adding your keys, execute the command

```bash
  '/usr/local/MirrorCommand/bin/showkeys'
```

The `showkeys` command will read the `mirrorkeys` file and edit the appropriate
configuration files in `/usr/local/MirrorCommand` containing the placeholder dummy
settings.

For more info on the `showkeys` command and the
`/usr/local/MirrorCommand/etc/mirrorkeys` configuration file, see the
man pages
`[showkeys.1](https://gitlab.com/doctorfree/MirrorCommand/-/wikis/showkeys.1)`
and
`[mirrorkeys.5](https://gitlab.com/doctorfree/MirrorCommand/-/wikis/mirrorkeys.5)`
by executing the `man` command:

`man showkeys`

`man 5 mirrorkeys`

Unfortunately, it is not possible to automate this process any further than is
done here with the `showkeys` command and `mirrorkeys` configuration file.
There are nearly 40 preconfigured dummy key values and corresponding empty keys
settings in the distributed `/usr/local/MirrorCommand/etc/mirrorkeys` file.
It is a tedious task to acquire all these keys but that is the state of the
art in 21st Century Internet services at this time. On the plus side, all of
these services can be obtained without charge. Perhaps in the future some
enterprising young entrepreneur will create a meta-service that can generate
keys for the myriad of services available via the web.

It is strongly recommended that you take the time to acquire those keys you
will need to access the services your MagicMirror will be activating prior to
or immediate following installation of the MirrorCommand package. It is not
necessary to obtain keys for all of the services, only those you may use.
For example, you may intend to deploy a MagicMirror as a News, Weather,
and Stock tracking display. In that case, the only keys you may need to
acquire might be an OpenWeather API key, Dark Sky API key, IEX Cloud API key,
and CoinMarketCap API key. Leaving all other key settings blank in the
`mirrorkeys` file will not effect display of activated and configured
services - it simply does not enable access to those services you do not use.

#### Configure mirror script

Edit the main MagicMirror management script,
**/usr/local/MirrorCommand/bin/mirror**, setting:

- Location of your MagicMirror installation
- IP address of your MagicMirror
- Port for your MMM-Remote-Control module
- MMM-Remote-Control API Key (this is configured by `showkeys` above)
- Configuration subdirectories

Defaults for these are:

- MM="${HOME}/MagicMirror"
- IP="MM.M.M.MM"
- PORT="8080"
- apikey="xxx_Remote-Control-API-Key_xxxxx"
- CONF_SUBDIRS="Artists JAV Models Photographers"

In most cases you will only need to set the MMM-Remote-Control API key.
The IP setting should have been configured properly during installation and the
MMM-Remote-Control API key is set by the `showkeys` command after the `mirrorkeys`
file has been configured with the API key.

If you have not configured an API key for MagicMirror remote control then
set the apikey to blank ( <code>apikey=</code> ).

#### Rerun initialization scripts

The MirrorCommand installation process attempts to configure the audio and
video display settings of the system. These configuration scripts can be
rerun post-installation if reconfiguration is desired. For example, if the
installation was performed in the absence of a running X server then the
video display settings may be incorrect. Or, if the audio settings changed
due to the addition of a USB audio device after installation then the audio
settings may need to be re-initialized.

To perform these adjustments post-installation rerun the initialization scripts.

To adjust the video display settings, execute the command:

`/usr/local/MirrorCommand/etc/set_mirror_screens`

The `set_mirror_screens` command will prompt for the display mode, Portrait
or Landscape, and configure the file `/usr/local/MirrorCommand/etc/mirrorscreen`.
This command should be run when the display setup changes. For example, if
an additional monitor is added to the system or the existing monitor is upgraded
with a higher resolution or display mode.

To adjust the audio input/output settings, execute the command:

`sudo /usr/local/bin/set_asound_conf -e`

The `set_asound_conf` command will provide a dialog to select the desired audio
output and input devices and configure the file `/etc/asound.conf`. This
command should be run when the audio setup changes. For example, if an audio
USB device is added to the system or you wish to change configured audio
input/output devices. This command can also be used to check the current
configuration with `sudo set_asound_conf -c`, restore the original configuration
with `sudo set_asound_conf -r`, and select a configuration for you with
`sudo set_asound_conf -e -n`. See `set_asound_conf -u` for a full usage message.

#### Image archive installation

See the [MirrorImages repository](https://gitlab.com/doctorfree/MirrorImages)
to download several packages that can be used to download image archives
preconfigured for use with the MirrorCommand config files. This is optional
and is provided simply as a convenience. Note that none of the MirrorImages
packages actually contain images. These packages know how to download
image archives when they are installed on a system and know where to
extract these archives so the MirrorCommand config files can access them.
Some MirrorImages archive downloads can consume significant disk space.
Make sure you have sufficient available disk space before installing.

## Custom Package Creation

You can create your own custom Debian and RPM format packages from
the repository source. To do so, clone the MirrorCommand repository:

<code>git clone ssh://gitlab.com/doctorfree/MirrorCommand.git</code>

or

<code>git clone `https://gitlab.com/doctorfree/MirrorCommand.git`</code>

Use the `mkpkg` script to create Debian and RPM format packages on a system
with the prerequisite packaging development environment. Once packages have
been created in the source repository they can be installed by executing the
`./Install` command. Packages can be removed with `./Uninstall`.

## Removal

On Debian based Linux systems where the MirrorCommand package was installed
using the MirrorCommand Debian format package, remove the MirrorCommand
package by executing the command:

```bash
    sudo apt remove mirrorcommand
```
or
```bash
    sudo dpkg -r mirrorcommand
```

**Note:** Removal may issue a warning about removing `/usr/local` and other
folders within `/usr/local`. This is an artifact of the Debian packaging system.
If you wish to silence that warning and prevent the Debian packaging system from
trying to remove `/usr/local` then install the
[core-custom-local Debian package](https://gitlab.com/doctorfree/core-custom-local/-/releases).

On RPM based Linux systems where the MirrorCommand package was installed
using the MirrorCommand RPM format package, remove the MirrorCommand
package by executing the command:

```bash
    sudo yum remove MirrorCommand
```
or
```bash
    sudo rpm -e MirrorCommand
```

## Supporting utilities and config files

There are several supporting scripts that can be used to enhance command
line capabilites. These are installed in `/usr/local/MirrorCommand/bin` with
symbolic links created in `/usr/local/bin`. Ensure that `/usr/local/bin`
is in your execution PATH.

Many sample MagicMirror configuration files are provided in the
**/usr/local/MirrorCommand/config** directory. The installation
package script attempts to link these into your MagicMirror config folder.
The sample config files use the naming convention `config-<name>.js`.

Several custom CSS files are provided in the `/usr/local/MirrorCommand/css directory.
Copy and modify as needed.

Some of the more useful supporting scripts include:

- **audiotest**
  Test the ALSA audio configuration by playing test sounds to each speaker
- **camsnap**
  Snap a photo with your MagicMirror webcam
- **chkconfig**
  Check your MagicMirror configuration files
- **chkinst**
  Check your Mirror Command Line installation
- **chktemp**
  Check your MagicMirror Raspberry Pi temperature
- **get_temps**
  Get your MagicMirror Raspberry Pi temperature
- **gethue**
  Get your Hue Hub properties
- **getquote**
  Get a stock symbol quote
- **mmapiactions**
  Get the MMM-Remote-Control API actions
- **mmgetb**
  Get the MagicMirror screen brightness level
- **mmsetb**
  Set the MagicMirror screen brightness level
- **myreboot**
  Perform additional actions before reboot, executed as a normal user using sudo
- **myshutdown**
  Perform additional actions before shutdown, executed as a normal user using sudo
- **rand_back**
  Select a random desktop wallpaper
- **set_asound_conf**
  Set the ALSA sound configuration in `/etc/asound.conf`
- **vncview**
  Remote script to start a VNC server on your MagicMirror and a VNC viewer on your desktop
- **vol**
  Script to control volume level of MagicMirror audio output
- **wireless_conf**
  Configure wireless using WPA Supplicant
- **wireless_dot_sample**
  Sample $HOME/.wireless to assist in wireless configuration

## Remote access

In order to remotely access the MagicMirror command line it is necessary to
setup SSH and associated SSH keys. That configuration is outside the scope
of this document. There are a number of guides on configuring SSH access on
a variety of systems. To get started with SSH configuration on a Raspberry Pi,
see https://www.raspberrypi.org/documentation/computers/remote-access.html

Once SSH access is configured, the **mm** script can be installed on
remote systems and used to remotely execute the mirror script on the system
hosting MagicMirror. All arguments provided to <code>mm</code> are simply
passed along to the <code>mirror</code> script.

Alternatively, the <code>mirror</code> script can be executed directly by a
user logging in to the MagicMirror system in a Shell environment (e.g. a
terminal window). This can be accomplished remotely in a terminal window
on the remote system by executing the ssh command. For example, using iTerm2
on a Mac OS X system, execute the command:

<code>ssh -l pi IP_ADDRESS</code>

where IP_ADDRESS is the IP address of the MagicMirror system. Once logged into
the MagicMirror system, the <code>mirror</code> command can be executed at a
shell command prompt:
<pre>
pi@raspberrypi:~ $ mirror
</pre>

Additional remote capabilities are provided through integration with the
[MMM-Remote-Control](https://github.com/Jopyth/MMM-Remote-Control) and
[MMM-TelegramBot](https://github.com/bugsounet/MMM-TelegramBot) modules.
Accessing and controlling your MagicMirror using these facilities is
described in the following sections.

#### Remote execution of mirror commands

If you wish to execute mirror commands remotely then install the convenience
script **mm** on a system with SSH access to your MagicMirror. This
script can be used to remotely execute the main mirror script.

#### Remote view of MagicMirror display

If you wish to view the MagicMirror display remotely then install the convenience
script **vncview** on a system with SSH access to your MagicMirror. This
script can be used to remotely execute a VNC server and locally execute a VNC client.

### MMM-Remote-Control integration

The `mirror` command line utilities can be integrated into a custom
[MMM-Remote-Control](https://github.com/Jopyth/MMM-Remote-Control) menu.
In this way the MMM-Remote-Control module can be extended to perform
many additional actions including taking a screenshot, rotating the
display, and controlling playback of video. This can, for example,
allow you to use your phone to control the MagicMirror while standing
in front of the mirror, away from your computer. Particularly handy
for taking screenshots.

The MMM-Remote-Control module provides some documentation on creating
a custom menu but it is currently incomplete. To add custom commands
to MMM-Remote-Control using the `mirror` command, see the
[MMM-Remote-Control Wiki Page](https://gitlab.com/doctorfree/MirrorCommand/-/wikis/Remote-Control-Custom-Menu).

#### MMM-TelegramBot integration
You can control your MagicMirrir with the `mirror` command executed remotely
using the Telegram app. This can allow you to control your MagicMirror from
anywhere by simply sending a message on your phone using the Telegram app.
To enable this feature, install the
[MMM-TelegramBot](https://github.com/bugsounet/MMM-TelegramBot)
module, setup a Telegram Bot to send and receive MMM-TelegramBot messages,
and add MMM-TelegramBot `customCommands` configuration to the MMM-TelegramBot
config section in `config/config.js`.

##### MMM-TelegramBot installation
Follow the instructions at the
[4th Party Modules Wiki](http://wiki.bugsounet.fr/en/MMM-TelegramBot)
to create a Telegram Bot, install MMM-TelegramBot, and configure your
MagicMirror `config.js` to enable Telegram commands.

##### MMM-TelegramBot module config

In addition to following the
[4th Party Modules Wiki Installation instructions](http://wiki.bugsounet.fr/en/MMM-TelegramBot/Installation)
to install the module and setup a Telegram Bot, the config section of the
MMM-TelegramBot module entry in `config.js` must be modified to add
`customCommands`. Samples of how to do this are in the config files in
this repository. For example, see the `customCommands` entry in
**config/config-default.js**.

Here is the section of the `customCommands` array definition in the config
section of the MMM-TelegramBot module entry in `config.js` that defines the
`/mirror` Telegram command:

```javascript
{
    command: 'mirror',
    description: "Executes MagicMirror `mirror` command\nTry `/mirror status`.",
    callback: (command, handler, self) => {
        if (handler.args) {
            var exec = "mirror -D " + handler.args
        } else {
            var exec = "mirror -D status"
        }
        handler.reply("TEXT", "Executing command: " + exec)
        var sessionId = Date.now() + "_" + self.commonSession.size
        if (exec) {
            self.commonSession.set(sessionId, handler)
            self.sendSocketNotification("SHELL", {
                session: sessionId,
                exec: exec
            })
        }
    },
},
```

##### MMM-TelegramCommands module

Configuring MMM-TelegramBot customCommands can be daunting. Use the template at
[MagicMirror/config/Templates/TelegramBot-customCommands.js](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/config/Templates/TelegramBot-customCommands.js)
as a guide.

Alternatively, several custom TelegramBot commands have been configured
and enabled in the
[MMM-TelegramCommands module](https://gitlab.com/doctorfree/MMM-TelegramCommands).
To enable the MMM-TelegramCommands module commands, install this module:

```bash
cd ~/MagicMirror/modules
git clone https://gitlab.com/doctorfree/MMM-TelegramCommands.git
cd MMM-TelegramCommands
npm install
```

After installing MMM-TelegramCommands add the following to the modules array
of any `config.js` that has MMM-TelegramBot activated:

```javascript
    {
        module: 'MMM-TelegramCommands'
    },
```

See this
[simple example of MMM-TelegramCommands configuration](https://gitlab.com/doctorfree/MMM-TelegramCommands/-/blob/master/examples/config-simple.js) as a guide.

##### Telegram usage
Once installed and configured, you can control your MagicMirror
by sending messages in the Telegram app to your previously created Telegram Bot.
If you copied the example MMM-TelegramBot customCommands configuration in
one of the config files in this repository then you will have three new
custom Telegram commands:

- /myReboot
    - Custom reboot command which executes /usr/local/bin/myreboot
- /myShutdown
    - Custom shutdown command which executes /usr/local/bin/myshutdown
- /mirror
    - General purpose command which executes the /usr/local/bin/mirror command with any arguments supplied in the Telegram command (e.g. `/mirror info` will retrieve your MagicMirror system information)

A few examples follow:

To switch the MagicMirror config.js to the configuration file
'config/config-sample.js', issue the Telegram command:

```
/mirror sample
```

To retrieve the MagicMirror status, issue the command:

```
/mirror status
```

To update the MagicMirror installation, issue the command:

```
/mirror update
```

To list the MagicMirror active modules, issue the command:

```
/mirror list active
```
Any `mirror` command can be executed via Telegram in this manner.
See `mirror -u` for the `mirror` usage message.

## MMM-GoogleAssistant integration
MirrorCommand includes configuration files to enable voice command
control of your MagicMirror utilizing the
[MMM-GoogleAssistant](http://wiki.bugsounet.fr/en/MMM-GoogleAssistant)
module. Most of the MagicMirror config files in the config subdirectory
come preconfigured with voice command support. See
**config/config-default.js** for a sample config
file with voice control enabled.

In addition to preconfigured config files, MirrorCommand provides several
custom MMM-GoogleAssistant recipes.
These include recipes to:
- Enable `mirror` command support via voice
    - Voice commands to:
	    - Restart MagicMirror
		- Rotate the screen
		- Turn the screen on/off
		- Mute/unmute sound
		- Copy custom config files into config.js and restart the mirror
        - Manage MagicMirror screen position on multi-screen systems
            - Move MagicMirror to screen 1
                - Say `screen one` or `mirror screen one`
            - Move MagicMirror to screen 2
                - Say `screen two` or `mirror screen two`
            - Switch the MagicMirror screen
                - Say `screen switch` or `switch screens` or `mirror screen switch`
- Voice management of MMM-Scenes scenes
    - Next scene
	- Previous scene
	- Scene by number (e.g. `scene 2`) 
- Customized reboot/restart/shutdown voice commands
- Radio station play via voice

### Google Cloud Platform API Keys
Several MagicMirror modules require a Google Cloud Platform API. The MMM-GoogleAssistant
and MMM-GoogleMapsTraffic modules are examples of these. In order to configure
the MMM-GoogleAssistant module you will need to create a Google Action project
and enable API services for that project in the Google Cloud Platform then generate
credentials for that project. This process can seem daunting to many but once you
walk through it the process becomes more transparent. A smart young woman has
provided us with a brief and simple tutorial walkthru of the process at
[https://youtu.be/xVhqP3fBnVM](https://youtu.be/xVhqP3fBnVM).
Her video is based on the
[4th Party Modules Wiki](http://wiki.bugsounet.fr/en/MMM-GoogleAssistant/GoogleAssistantSetup)
description of this process.

**NOTE:** When authorizing the YouTube access token with `npm run tokens` as the final
step in this process, I found it necessary to modify
MMM-GoogleAssistant/install/auth_YouTube.js
to add a console log output of the generated URL to allow access. This was necessary
in my case because I was performing the process over an SSH connection in a terminal.
This is not necessary if you are accessing the MagicMirror directly or if you have
your DISPLAY set back to the system on which you are running SSH. If you need to use
this modification, it can be found at the link above.

## [MMM-Scenes](https://github.com/MMRIZE/MMM-Scenes#readme) integration

In addition to the voice control of MMM-Scenes described above, several `mirror`
commands have been added to support management of MMM-Scenes scenes via the
command line. Supported commands include:
- `mirror scene next` : display the next scene in the scenario
- `mirror scene prev` : display the previous scene in the scenario
- `mirror scene name` : display the scene named 'name'
- `mirror scene num`  : display scene number 'num'
- `mirror scene info` : retrieve info on MMM-Scenes configuration

## Usage

The `mirror` shell script is installed on any MagicMirror system that you want
to utilize for command line control of your MagicMirror. Remote execution of
the `mirror` command line script may be accomplished by using the "mm"
convenience script on a remote system with SSH access to your MagicMirror.

Here is the current output of "mirror -u" which displays a usage message.

```
Usage: mirror <command> [args]

Where <command> can be one of the following:
    info <temp|mem|disk|usb|net|wireless|screen>
    list <active|installed|configs>
    rotate <right|left|normal|inverted|default>
    scene <next|prev|info|name|number>
    screen <on|off|info|status>
    stop|start|restart|mute|unmute|screenshot|reboot|shutdown
    playvideo|pausevideo|nextvideo|replayvideo|hidevideo|showvideo
    update [modules]
    vol <percent>|mute|unmute|save|restore|get
    dev | getb | setb <num> | select | status <all> | youtube
    artists_dir, models_dir, photogs_dir
    ac|ar <artist>, jc|jr <idol>, mc|mr <model>, pc|pr <photographer>, wh|whrm <dir>

Specify a config file to use by executing a command of the form:

	mirror <name>

where <name> is one of:
	 all Artists art background bikini blank calendar candy covid
	 crypto openweather default face fractals gif iframe instagram ironman
	 JAV Models nature networkcols network networktest news nokeys normal
	 owls Photographers pics portal radar rooncontrol roon scenes scnews
	 scoreboard screencast server smoke snowcrash stocks swimweek tantra test
	 traffic videotest voice volumio waterfalls weather YouTube

or any other config file you have created in /usr/local/MagicMirror/config of the form:

	config-<name>.js

A config filename argument will be resolved into a config filename of the form:

	config-$argument.js

A subdirectory in which to locate the config file can be specified as the second argument, e.g. 'mirror foo bar' will attempt to use the config file bar/config-foo.js

The mirror command will attempt to match the specified config file name. For example, 'mirror foo' would match the config file named config-food.js

Arguments can also be specified as follows:

	-a <artist>, -A <artist>, -b <brightness>, -B, -c <config>, -d, -i <info>,
	-V, -N, -R (toggle video play, play next video, replay video),
	-H, -h (Hide video, Show video),
	-L, use landscape display mode and use landscape designed configs/pics,
	-I, -l <list>, -r <rotate>, -s <screen>, -S, -m <model>, -M <model>,
	-p <photographer>, -P <photographer>, -w <dir>, -W <dir>
	-X <screen number>, -Z, -u

Examples:

	mirror		# Invoked with no arguments the mirror command displays a command menu
	mirror list active		# lists active modules
	mirror list configs		# lists available configuration files
	mirror restart		# Restart MagicMirror
	mirror fractals		# Installs configuration file config-fractals.js and restarts MagicMirror
	mirror info		# Displays all MagicMirror system information
	mirror info screen		# Displays MagicMirror screen information
	mirror dev		# Restarts the mirror in developer mode
	mirror rotate left/right/normal/inverted/default		# rotates the screen left, right, inverted, normal, or restores all screens to their default rotation
	mirror screen on		#  Turns the Display ON
	mirror screen off		# Turns the Display OFF
	mirror screenshot		# Takes a screenshot of the MagicMirror
	mirror screen num		# Switches mirror display to screen num
	mirror status [all]		# Displays MagicMirror status, checks config syntax
	mirror update		# Updates MagicMirror installation
	mirror update modules		# Updates installed MagicMirror modules
	mirror getb		# Displays current MagicMirror brightness level
	mirror setb 150		# Sets MagicMirror brightness level to 150
	mirror vol 50		# Sets MagicMirror volume level to 50
	mirror wh foobar		# Creates and activates a slideshow config with pics in foobar
	mirror whrm foobar		# Deactivate and remove slideshow in foobar
	mirror -u		# Display this usage message
```

### Getting to the Command Line

Learn how to open a command line terminal window on various systems,
how to get started using the command line, and see some examples of why
the command line interface is so powerful by reading the MirrorCommand
wiki article
[Introduction to Using the Command Line](https://gitlab.com/doctorfree/MirrorCommand/-/wikis/Introduction-to-Using-the-Command-Line).

Note that some screen switching operations on systems with multiple monitors
may move the window focus from the command line terminal window to the
MagicMirror window. When this happens the mouse and keyboard input are no
longer being sent to the terminal window. To restore focus in the terminal
window, move the mouse cursor over the terminal window and click.

If your terminal window is obscured by the fullscreen MagicMirror window
and you wish to return to the terminal window, press &lt;F11&gt; to exit
MagicMirror fullscreen and click the mouse in the terminal window.

### Switching screens

On systems with more than one monitor it is possible to move the MagicMirror
window from one screen to another. Screens are numbered starting with '1' so
the primary screen display is screen number 1 and the secondary screen
is screen number 2. Naturally, this does not correspond to the internal
numbers assigned to screens which start with '0'. The wise geeks at
Doctorwhen's Bodacious Laboratory always start counting things at 1, not 0.
They thought you might also.

#### Using the mirror command to switch screens

You can use the `mirror` command to switch screens. For example, to move
the MagicMirror window from the primary screen to the secondary screen,
execute the command `mirror screen 2`. To switch screens without knowing
which screen is number 1 and which is number 2, execute the command
`mirror screen switch` or `mirror switch`.

To start MagicMirror on a specified screen execute the command:

`mirror -X <screen_number> ...`

#### Using voice commands to switch screens

The `MirrorCommand` package installs several `MMM-GoogleAssistant` voice
recipes. One of these, the `MirrorCommand.js` recipe, enables several voice
commands that can be used to control the MagicMirror. See the section
[MMM-GoogleAssistant integration](#mmm-googleassistant-integration)
to get started with MMM-GoogleAssistant setup and integration.

Once you have MMM-GoogleAssistant working and you can talk to your mirror
and get a response from Google Assistant, you can add the `MirrorCommand.js`
recipe to the MagicMirror `config.js` to issue MirrorCommand voice commands.

Among the MirrorCommand voice commands there are the following which control
screen switching:

Assuming your `MMM-GoogleAssistant` key phrase ('Model' config value) is "computer",

- Move MagicMirror to screen 1
    - Say `computer` and pause
    - Say `screen one` or `mirror screen one`
- Move MagicMirror to screen 2
    - Say `computer` and pause
    - Say `screen two` or `mirror screen two`
- Switch the MagicMirror screen
    - Say `computer` and pause
    - Say `screen switch` or `switch screens` or `mirror screen switch`

## Documentation

Many MirrorCommand commands have manual pages. Execute `man <command-name>`
to view the manual page for a command. The `mirror` frontend is the primary
user interface for the MirrorCommand commands and the manual page for
`mirror` can be viewed with the command `man mirror`. Most commands also have
help/usage messages that can be viewed with the **-u** argument option,
e.g. `mirror -u`.

The manual page for the primary MirrorCommand user interface, `mirror`,
can be viewed by executing the command:

- `man mirror`

Manual pages for these MirrorCommand commands can be viewed by executing
any of the following commands (click to view the man page online):

- [man mirror](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/mirror.1.md)
- [man 5 mirrorkeys](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/mirrorkeys.5.md)
- [man set_asound_conf](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/set_asound_conf.1.md)
- [man mmscene](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/mmscene.1.md)
- [man mmscreen](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/mmscreen.1.md)
- [man showkeys](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/showkeys.1.md)
- [man vol](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/vol.1.md)
- [man websnap](https://gitlab.com/doctorfree/MirrorCommand/-/blob/master/markdown/websnap.1.md)

## Motivation

### Introduction to Using the Command Line
The command line has a long and storied history in computing. Read some of that
history, learn how to open a command line terminal window on various systems,
how to get started using the command line, and see some examples of why the command
line interface is so powerful by reading the MirrorCommand wiki article
[Introduction to Using the Command Line](https://gitlab.com/doctorfree/MirrorCommand/-/wikis/Introduction-to-Using-the-Command-Line).

This introduction to the command line includes an example of how to automate
display of a specified menu on a MagicMirror at designated times of day.

### Why would I need or want command line control of MagicMirror

One might reasonably ask "Why would I need or want command line control
of my MagicMirror"? Truth be told, most MagicMirror users do not need or
want command line control of MagicMirror or any other software. They are happy
with the graphical user interfaces they use and never ever see a command
line prompt. So the answer to that question is almost always "You don't".

However, some users (mostly old propeller head codgers) are comfortable
at the command line and prefer to use it over the tedious mouse clicks
required to get anything done in a graphical user interface. Different
lanes for different brains.

I would say the most significant use case for command line control of anything
is automation. For example, if I want to schedule playback of specified music
in specific zones triggered by some event, then command line control can be
used to implement this. That can be done via Cron jobs, play something in some
zone at scheduled times. Or playback of specified songs in selected zones could
be triggered by some event like when a particular face is recognized by my smart
mirror or when my smart lights are turned to a particular profile. I use command
line control of MagicMirror coupled with Apple Siri voice commands that trigger
an SSH shortcut to run the command. There are many use cases for automation using
command line utilities.

The other main use case for command line control is simple convenience.
If you spend a lot of time in a Shell environment then it is just easier
to type a command that plays what you would like to hear where you want
to hear it than it is to switch windows, bring up a GUI, click a few times
to find what you want, and click to play it, then go back to your terminal
window and Shell env. Most people do not live in a Shell environment like
I do so this use case is not that significant.

Finally, the command line interface and the associated MagicMirror API can provide
capabilities not otherwise available. Searching, listing, and filtering
can be augmented by the plethora of tools available in a typical Shell
environment. You can pipe the output of a `mirror` command to grep, sed, awk,
and other standard utilities to produce results difficult to achieve otherwise.
That is, command line control along with the API and Shell utilities/builtins
can extend the capabilities of the MagicMirror system. The MirrorCommand
package also enables some features not easily available in MagicMirror.
One of these, management of a large number of preconfigured MagicMirror config files,
allows the MirrorCommand user to easily and quickly switch between any of these
preconfigured config files. In my household I find it frequently desirable to be able
to switch MagicMirror configs easily and quickly and I can do so by configuring these
presets to my typical use cases and executing a simple `mirror` command.

### History

This project began as an attempt to control my MagicMirror with Siri voice
commands. I was able to get Siri voice control of a MagicMirror working with
simple SSH shortcuts that execute Bash scripts on my mirror's Raspberry Pi.
Apple’s SSH shortcuts are a powerful tool for command line control. They can
be used to execute commands on systems that allow SSH access and they can
be configured to activate via voice commands. SSH shortcuts enable voice
control of anything that can be done at the command line.

I created shortcuts on my iPhone which use the “Run script over SSH”
option for Apple Scripting shortcuts. The shortcuts execute the appropriate
Bash command on my MagicMirror Pi. Once I got the MagicMirror shortcuts working
I then configured Siri to recognize various phrases to run those shortcuts.
In this manner I was able to implement Siri voice control of my MagicMirror.

Over time the project became primarily focused on the command line execution
of these scripts as I found I spend more time in a terminal at the command line
than I do talking to Siri. While voice control is still supported if configured
properly, the project is primarily command line control of MagicMirror.

Recent releases have focused on automated installation and configuration as well
as configuration based upon auto-detected system features. Some aspects of the
automated installation of MagicMirror drew upon previous work by Sam Detweiler
in his [MagicMirror scripts project](https://github.com/sdetweil/MagicMirror_scripts).

## Contents

See the [MirrorCommand Contents](https://gitlab.com/doctorfree/MirrorCommand/-/wikis/MirrorCommand-Contents) wiki page for a full contents listing.

## Known Limitations

The following are known limitations in the current release:

- The installation packages are interactive and cannot be integrated into an unattended install process
- The MirrorCommand config files are modified by the `showkeys` command in a manner that prevents subsequent key value changes and a rerun of `showkeys`
    - A key value can be added to an empty key array entry and `showkeys` rerun
    - Once a key value has been set in `mirrorkeys` and `showkeys` has been run, that value is hard coded in all config files that use it
- If a secondary monitor is attached but the system does not recognize it as "connected" then it will not be added to the `mirrorscreens` config file and the `mirror` command will not recognize it
    - In some cases it is necessary to power on the monitor prior to booting the system in order for the X11 graphical system to recognize the monitor
- Significant effort has been made to adjust the module layouts in all config files to create a MagicMirror display with non-overlapping regions. However, some screen resolutions may need manual adjustment of some config files to arrive at a pleasant display. Testing has been limited to only a few screen resolutions and display modes.
- The current release does not fully support seamless upgrades nor have upgrades been thoroughly tested. If a future upgrade of the MirrorCommand package fails or does not entirely complete, the recommended procedure is to backup all MagicMirror and MirrorCommand files, remove the MirrorCommand package, and install the newer MirrorCommand package.

## Screenshots

<p float="left">
Sample default and weather configs<br/>
  <img src="https://github.com/doctorfree/MirrorCommand/blob/master/screenshots/mirror_default.png?raw=true"/>
  <img src="https://github.com/doctorfree/MirrorCommand/blob/master/screenshots/mirror_weather.png?raw=true"/>
</p>
<p float="left">
Interactive menus when invoked with no arguments<br/>
  <img src="https://github.com/doctorfree/MirrorCommand/blob/master/screenshots/mirror_command_menu.jpg?raw=true"/>
  <img src="https://github.com/doctorfree/MirrorCommand/blob/master/screenshots/mirror_submenu.jpg?raw=true"/>
</p>

## License

Copyright: 2014-2022 Ronald Joe Record <ronaldrecord@gmail.com>

License: MIT

## See also

- [MagicMirror](MagicMirror.md)
- [Raspberry Pi](../linux/raspberry-pi.md)
- [Asciiville](Asciiville.md)
- [MusicPlayerPlus](MusicPlayerPlus.md)
- [DriveCommandLine](DriveCommandLine.md)
- [RoonCommandLine](RoonCommandLine.md)
