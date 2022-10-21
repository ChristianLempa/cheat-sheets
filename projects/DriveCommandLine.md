---
tags:
  - bash
  - cloud
  - gdrive
  - go
  - linux
  - projects
  - commandline
  - command-line
  - google
  - sync
  - shell
  - cli
  - productivity
  - archiving
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

# DriveCommandLine
This repository maintains a collection of scripts to initialize,
configure, monitor, and manage Google Drive. The packaging includes
a build of the [gdrive command line utility](https://github.com/prasmussen/gdrive).
DriveCommandLine provides several user-friendly features such as native platform
intallation packaging and wrapper scripts that hopefully make the gdrive
utility easier to use. The gdrive binary included in the installation packages
is built from the latest version of the original gdrive repository maintained
by Petter Rasmussen. No changes have been made to the gdrive utility and its
use is described below. What you are getting here is packaging for ease of
installation and maintenance along with user-friendly wrapper scripts and
documentation.

## Table of contents

1. [Overview](#overview)
1. [News](#news)
1. [Prerequisites](#prerequisites)
1. [Quick start guide](#quick-start-guide)
1. [Installation](#installation)
    1. [Debian package installation](#debian-package-installation)
    1. [RPM package installation](#rpm-package-installation)
    1. [Manual installation](#manual-installation)
    1. [Installation from source](#installation-from-source)
1. [Initial setup](#initial-setup)
    1. [Authentication and access](#authentication-and-access)
    1. [DriveCommandLine GDHOME local storage location](#drivecommandline-gdhome-local-storage-location)
1. [Documentation](#documentation)
1. [Motivation](#motivation)
    1. [Introduction to Using the Command Line](#introduction-to-using-the-command-line)
    1. [Why would I need or want command line control of Google Drive](#why-would-i-need-or-want-command-line-control-of-google-drive)
    1. [Why would I need or want the DriveCommandLine wrappers](#why-would-i-need-or-want-the-drivecommandline-wrappers)
1. [Usage](#usage)
    1.  [Getting started](#getting-started)
    1.  [Direct invocation of gdrive](#direct-invocation-of-gdrive)
    1. [Synopsis of gdrive command](#synopsis-of-gdrive-command)
    1. [Synopsis of DriveCommandLine commands](#synopsis-of-drivecommandline-commands)
    1. [Examples](#examples)
1. [Example application](#example-application)
1. [Limitations](#limitations)
1. [Troubleshooting](#troubleshooting)
1. [Compile from source](#compile-from-source)
    1. [Cool feature used by this repository](#cool-feature-used-by-this-repository)
1. [Removal](#removal)
1. [See also](#see-also)

## Overview
The DriveCommandLine package includes gdrive, a command line utility for
interacting with Google Drive and several wrapper scripts for easily performing
many of the Google Drive management tasks the gdrive utility enables from
the command line.

The DriveCommandLine Debian and RPM format installation packages automate
the installation and configuration process.

Currently DriveCommandLine and control scripts include support for:

- Creating local folder IDs for each Google Drive folder or specified folders
- Retrieving info on files or folders in Google Drive by file/folder name
- Listing, downloading, uploading, and removing Google Drive files and folders
- Syncing specified folders to Google Drive
- Syncing from Google Drive
- Retrieving Google Drive folder IDs
- Creation and maintenance of Google Drive sync folders
    - `sync2drive` and `gdupload` can create sync folders from existing non-empty Google Drive folders
    - `sync2drive` and `gdupload` can upload to Google Drive sync folders without limitation
- Unix style manual pages for all commands (see the [DriveCommandLine wiki](https://gitlab.com/doctorfree/DriveCommandLine/-/wikis/home))

## News
### Jan 05, 2022
DriveCommandLine supports installation package and distribution archives
for multiple platforms and architectures including:

aix_ppc64, android_amd64, android_arm64, darwin_amd64,
darwin_arm64, dragonfly_amd64, freebsd_386, freebsd_amd64, freebsd_arm64,
freebsd_arm, illumos_amd64, js_wasm, linux_386, linux_amd64, linux_arm64,
linux_arm, linux_mips64, linux_mips64le, linux_mips, linux_mipsle,
linux_ppc64, linux_ppc64le, linux_riscv64

### May 28, 2021
the `gdrive` project is verified for using sensitive scopes which should
fix the `This app is blocked` error. Note that the project name will show
up as `project-367116221053` when granting access to you account.

## Prerequisites

The DriveCommandLine utilities require `/bin/bash`, the Bash Shell, and
standard Unix/Linux system utilities like `grep`, `sed`, and `awk`.
These requirements are met by almost every Unix and Linux distribution.

The `gdrive` binary has no prerequisites as it is statically linked.

On almost all platforms there should be no prerequisite to running
the DriveCommandLine utilities other than a network connected, standard
operating system environment. It should even be possible to deploy
one of the DriveCommandLine distribution archives on a Microsoft
Windows platform under the Linux subsystem but this has not been tested.

If you want to [compile from source](#compile-from-source) you need the
[go toolchain](http://golang.org/doc/install) version 1.5 or higher.

## Quick start guide

There is a wealth of information available in this document, the wiki, and the
DriveCommandLine documentation but users already familiar with `gdrive` may
wish to quickly jump to installing and setting up DriveCommandLine. This quick
start guide assumes you have a good familiarity with systems, architectures,
and the installation process. It provides only the basic steps necessary
to install, setup, and use DriveCommandLine. Skip to the
[Installation](#installation) section below for greater detail.

1. Visit
[DriveCommandLine releases](https://gitlab.com/doctorfree/DriveCommandLine/-/releases)
and download the latest release for your platform and architecture

2. Install the release using the appropriate installation command, e.g. `apt`,
`dpkg`, `rpm`, `yum`, `tar`, `unzip`, or other command supporting the format
of the downloaded distribution archive

3. Generate a Google Drive access token by executing the `gdrive about` command

4. Configure a local DriveCommandLine folder to mirror Google Drive folders by
executing the `gdlist` command

5. Execute the `getfolderids` command

Repeat steps 3-5 for any additional Google Drives you wish to manage.
When adding an additional Google Drive, use the `-c configdir` option
to `gdrive`, `gdlist`, and `getfolderids`. For example:

`gdrive -c ~/.gdrive-secondary about`

`gdlist -c ~/.gdrive-secondary`

`getfolderids -c ~/.gdrive-secondary`

## Installation

DriveCommandLine can be installed on Linux systems using
either the Debian packaging format or the Red Hat Package Manager (RPM).
Other systems will require a manual installation described below.

The `gdrive` binary is operating system and architecture specific. To
determine which OS/architecture installation package or archive to install,
run the following commands.

### Operating system

`uname -o` should return an operating system name. On Linux systems this will
usually be "GNU/Linux" while on Mac OS X it will be "Darwin". The distribution
archives use the lower case operating system names of "linux" and "darwin".

### Architecture

On Debian based systems (Ubuntu Linux, etc):

`dpkg --print-architecture` will return the native architecture.

On RPM based systems (Redhat/CentOS/Fedora Linux, etc):

`rpm --eval '%{_arch}'` will return the native architecture.

On Mac OS X the GO architectures supported do not match those returned by
the standard system commands. Go figure. To find your architecture on a Mac
execute the `uname -m` command. If it returns something like "x86_64" then
use the "darwin_amd64" DriveCommandLine distribution archive. If it returns
something with "arm" in the architecture then use the "darwin_arm64"
distribution archive.

DriveCommandLine distribution archives exist for a wide variety of operating
system platforms and architectures. If it is not clear what distribution
archive is targeted for your platform then raise an issue at
https://gitlab.com/doctorfree/DriveCommandLine/-/issues

### Debian package installation

Many Linux distributions, most notably Ubuntu and its derivatives, use the
Debian packaging system.

To tell if a Linux system is Debian based it is usually sufficient to
check for the existence of the file `/etc/debian_version` and/or examine the
contents of the file `/etc/os-release`.

To install on a Debian based Linux system, download the latest Debian format
package from the
[DriveCommandLine Releases](https://gitlab.com/doctorfree/DriveCommandLine/-/releases).

Install the DriveCommandLine package by executing the command

```bash
sudo apt install ./DriveCommandLine_<version>-<release>.<arch>.deb
```
or
```console
sudo dpkg -i ./DriveCommandLine_<version>-<release>.<arch>.deb
```

### RPM package installation

Red Hat Linux, SUSE Linux, and their derivatives use the RPM packaging
format. RPM based Linux distributions include Fedora, AlmaLinux, CentOS,
openSUSE, OpenMandriva, Mandrake Linux, Red Hat Linux, and Oracle Linux.

To install on an RPM based Linux system, download the latest RPM format
package from the
[DriveCommandLine Releases](https://gitlab.com/doctorfree/DriveCommandLine/-/releases).

Install the DriveCommandLine package by executing the command

```bash
sudo yum localinstall ./DriveCommandLine_<version>-<release>.<arch>.rpm
```
or
```console
sudo rpm -i ./DriveCommandLine_<version>-<release>.<arch>.rpm
```

### Manual installation

Download the latest compressed tar archive release for your platform
from the latest
[DriveCommandLine Releases](https://gitlab.com/doctorfree/DriveCommandLine/-/releases).

As root, extract the archive. For example, to install
from a gzip'd tar archive:

```bash
sudo tar -ompxzf /path/to/DriveCommandLine_<version>-<release>.<os>_<arch>.tgz -C /
```

### Installation from source

To install DriveCommandLine from source the system must satisfy the requirements
described below in the [Compile from source](#compile-from-source) section. Once
the GO toolchain and appropriate packaging tools are installed:

```bash
git clone https://gitlab.com/doctorfree/DriveCommandLine.git
cd DriveCommandLine
./mkpkg
./Install
```

The `./Install` script attempts to derive the platform operating system and
architecture and install the appropriate distribution archive. If it fails to
find a matching distribution archive it will list what it thinks are packages
available for your platform. Follow the instructions above for a manual
installation using the appropriate distribution archive for your platform.

## Initial setup

After installing DriveCommandLine it is necessary to perform a couple
of one-time initialization setup tasks. The `gdrive` app must be given
access rights to Google Drive and the DriveCommandLine utilities need
to know where the local Google Drive storage folders reside.

### Authentication and access

The first time gdrive is launched (i.e. run `gdrive about` in your
terminal not just `gdrive`), you will be prompted for a verification code.
The code is obtained by following the printed url and authenticating with the
google account for the drive you want access to. This will create a token file
inside the .gdrive folder in your home directory. Note that anyone with access
to this file will also have access to your google drive.

If you want to manage multiple drives you can use the global `-c configdir`
flag or set the environment variable `GDRIVE_CONFIG_DIR`.

**Example:** `GDRIVE_CONFIG_DIR="/home/user/.gdrive-secondary" gdrive list`

You will be prompted for a new verification code if the folder does not exist.

All of the DriveCommandLine commands obey these same rules. On first invocation
they will prompt for initialization requirements if not previously set and
multiple Google Drives can be managed via either the `-c configdir` flag or
the environment variable `GDRIVE_CONFIG_DIR`.

**Examples:**

`GDRIVE_CONFIG_DIR="/home/user/.gdrive-secondary" getfolderids`

`getfolderids -c /home/user/.gdrive-secondary`

### DriveCommandLine GDHOME local storage location

The DriveCommandLine utilities use the environment variable **GDHOME**
to access the locally stored mirror of the Google Drive they manage.
This variable is set in the file `$HOME/.gdrive/gdhome`

To initialize this setting execute any of the DriveCommandLine utilities.
If this variable has not previously been configured, the utility will
prompt you for a path to your local Google Drive storage. For example,
execute the command `gdlist`. If no GDHOME has been set the command will
prompt you to Initialize gdrive home to the current working directory.
If that is where you wish to maintain local Google Drive storage then
enter 'y' or 'Y'. If you prefer another location for local storage then
enter 'n' or 'N' and you will be prompted to "Enter your gdrive home".
Enter the full absolute path to your gdrive home and your GDHOME will
be configured in `$HOME/.gdrive/gdhome`.

These two initialization steps need only be performed once, prior to first
use of the system. Subsequent invocations of `gdrive` or the DriveCommandLine
utilities should not require further initialization unless you wish to
change the location of your local storage or the authentication token expires.

Once you have initialized DriveCommandLine you can populate your local storage
folder with Google Drive folder IDs by running the `getfolderids` command.

## Documentation

Many DriveCommandLine commands have manual pages. Execute `man <command-name>`
to view the manual page for a command. Most commands also have help/usage messages
that can be viewed with the **-u** argument option, e.g. `sync2drive -u`.

Manual pages for these DriveCommandLine commands can be viewed by executing
any of the following commands (click to view the man page online):

- [man gdget](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/gdget.1.md)
- [man gdinfo](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/gdinfo.1.md)
- [man gdlist](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/gdlist.1.md)
- [man gdrm](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/gdrm.1.md)
- [man gdshare](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/gdshare.1.md)
- [man gdupload](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/gdupload.1.md)
- [man getfolderids](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/getfolderids.1.md)
- [man sync2drive](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/sync2drive.1.md)
- [man sync_from_drive](https://gitlab.com/doctorfree/DriveCommandLine/-/blob/master/markdown/sync_from_drive.1.md)

## Motivation

Google Drive is a ubiquitous cloud storage and synchronization service which
offers anyone with a free GMail account 15GB of free cloud storage through
Google One. However, managing a Google Drive can be difficult, especially
for those users with multiple GMail accounts and Google Drives.

This package intends to provide Google Drive management via the command line
in a manner that eases the burden of Google Drive management and provides
a facility to automate many Google Drive management tasks.

### Introduction to Using the Command Line

The command line has a long and storied history in computing. Read some of that
history, learn how to open a command line terminal window on various systems,
how to get started using the command line, and see some examples of why the command
line interface is so powerful by reading the DriveCommandLine wiki article
[Introduction to Using the Command Line](https://gitlab.com/doctorfree/DriveCommandLine/-/wikis/Introduction-to-Using-the-Command-Line).

### Why would I need or want command line control of Google Drive

Google Drive provides an easy to use graphical user interface. There is
a browser based user interface and Google Drive apps for most platforms.
These work well enough and suffice for basic upload, download, and sync.

Some users (mostly old propeller head codgers) are comfortable at the
command line and prefer to use it over the tedious mouse clicks required
to get anything done in a graphical user interface.
Different lanes for different brains.

Typically the most significant use case for command line control of anything
is automation. For example, command line control of a service can be used to
schedule uploads/downloads/sync/whatever triggered by some event - time of
day or day of week or modified file/folder. But Google Drive for Desktop
takes care of automated synchronization fairly well.

With Google Drive, for me, the case for command line control is somewhat
different than simple automation. Google Drive presents its own mysteries
and difficulties. For example, scripted/programmatic downloads of files
and folders require the knowledge of the file/folder ID in Google Drive.
That is, Google Drive doesn't uniquely identify assets by name or path
but by an id. The id can be obtained by examining the Google Drive share
link and trimming off most of the url. That's a tedious operation if you
have very many files you wish to add to a programmatic download. Further
complicating matters, in Google Drive two unique and different files or
folders can have the exact same path and name with different IDs.

The primary case for command line control of Google Drive, for me, is the
ability to script/program Google Drive actions. Yes, there is an API and
one could employ the API but that requires significant effort and can be
prone to error.
[Petter Rasmussen's gdrive](https://github.com/prasmussen/gdrive)
has already implemented an excellent command line Google Drive interface
so why not just use that?

Scripting Google Drive actions is especially useful when there are many
files and folders to maintain. For example, if I need to publicly share
several hundred files but privately hide some others in a folder, to do
so manually in the Google Drive app or web interface is extremely tedious.
I can perform this action quickly and easily with a scripted command line.

For some, a good reason for command line control is simple convenience.
If you spend a lot of time in a Shell environment then it is just easier
to type a command that does what you would like than it is to switch windows,
bring up a GUI, click a few times to find what you want, and click to
get it done, then go back to your terminal window and Shell env.

Finally, the command line interface and the associated Google Drive API
can provide capabilities not available in the Google Drive GUI. Searching,
listing, and filtering can be augmented by the plethora of tools available
in a typical Shell environment. You can pipe the output of a `gdrive` command
to grep, sed, awk, and other standard utilities to produce results unavailable
in the GUI. That is, command line control along with the API and Shell
utilities/builtins can extend the capabilities of the Google Drive file
storage and synchronization service.

### Why would I need or want the DriveCommandLine wrappers

Ok, so now we are convinced command line control of Google Drive can be
of benefit. What value, if any, do the DriveCommandLine wrapper scripts
provide? Can't I just use the `gdrive` command with all its useful
features and options? Why install this extra package?

The DriveCommandLine package scripts provide significantly improved usage
over direct invocation of `gdrive`. Many of the operations carried out by
`gdrive` require the Google Drive file or folder ID as an argument to the
command. Often the Google Drive user knows the name of the file/folder but
seldom to we know its ID. We can discover it but it is tedious to do so.
The DriveCommandLine commands wrap the `gdrive` command in a way that
abstracts the Google Drive IDs of files and folders. They allow you to address
your Google Drive files and folders by name and path rather than by ID.

DriveCommandLine commands get around some of the irritating "features"
of Google Drive in a safe and secure manner. For example, Google Drive
and, by extension, the `gdrive` command, will not create a sync folder
for an existing non-empty Google Drive folder. The DriveCommandLine commands
`sync2drive` and `gdupload` overcome this limitation and enable the creation
of sync folders to existing non-empty Google Drive folders wihout losing content.

Furthermore, many `gdrive` commands require a query to identify the Google
Drive asset(s) to act upon. These queries can be difficult to construct and
prone to error. The DriveCommandLine utilities attempt to alleviate this
requirement on the part of the user and construct the appropriate queries
based upon the command line arguments and detected Google Drive IDs.

Finally, the DriveCommandLine utilities not only wrap `gdrive` in a user
friendly and protected manner but extend the capabilities of command line
control of Google Drive. This is primarily accomplished by initializing
a mirror of the user's Google Drive folders in local storage. Each mirrored
local folder is populated with its Google Drive ID. These locally stored
Google Drive IDs can be used to quickly and easily traverse a user's
Google Drive and locate where and if actions should be performed. Other
extensions such as detecting the potential for duplicate file or folder
name creation in Google Drive are also implemented in DriveCommandLine.

## Usage

### Getting started

To get started with DriveCommandLine management of Google Drive, invoke any of
the DriveCommandLine wrapper scripts. These currently include:

- `gdget` - download files/folders from Google Drive
- `gdinfo` - get info on Google Drive files and folders
- `gdlist` - list Google Drive files and folders
- `gdrm` - remove Google Drive files and folders
- `gdshare` - manage share permissions for Google Drive files and folders
- `gdupload` - upload files and folders to Google Drive
- `getfolderids` - retrieve Google Drive folder IDs and populate local folders with IDs
- `sync2drive` - sync local files and folders to Google Drive (upload)
- `sync_from_drive` - sync Google Drive files and folders to local storage (download)

The initial invocation of a DriveCommandLine command will prompt to initialize
gdrive home, providing the current working directory as the default. Either accept
the default and use the current working directory as your gdrive home or enter
a path to where you want to manage Google Drive locally. This location, the
"gdrive home", is where local files and folders will be stored and where folder
IDs will be maintained. It can be any folder, preferably not one with other
unrelated work in it and a location with sufficient disk space for your
Google Drive activity.

Once the "gdrive home" has been set and stored in the file `~/.gdrive/gdhome`
and `gdrive` has been authenticated and access granted (see the section on
[Authentication and access](#authentication-and-access)), initialize the local
Google Drive storage home by executing the `getfolderids` command.

This will populate your configured gdrive home with folders that mirror your
Google Drive folders and folder IDs in the file `.folderid` in each of the
mirrored folders.

See the [Documentation section](#documentation) for links to the man pages
for several of the DriveCommandLine commands.

### Direct invocation of gdrive

Most of the actions performed by the DriveCommandLine commands are carried out
by the `gdrive` command. The DriveCommandLine commands simply act as a user
friendly front-end to `gdrive`. All of these actions can be performed by directly
invoking the `gdrive` command if you know the required command syntax and in
many cases, the Google Drive file or folder ID.

The DriveCommandLine utilities do not yet implement every feature and option
supported in `gdrive`. It may on occasion be necessary to invoke `gdrive`
directly to accomplish a task.

An in depth review of `gdrive` command usage along with documentation
and example usage of the `gdrive` command is available in the
[DriveCommandLine wiki man page for gdrive](https://gitlab.com/doctorfree/DriveCommandLine/-/wikis/gdrive.1). The gdrive man page is also available via the
`man` command by executing the command `man gdrive`.

### Synopsis of gdrive command

```
gdrive [global] list [options]                                 List files
gdrive [global] download [options] <fileId>                    Download file or directory
gdrive [global] download query [options] <query>               Download all files and directories matching query
gdrive [global] upload [options] <path>                        Upload file or directory
gdrive [global] upload - [options] <name>                      Upload file from stdin
gdrive [global] update [options] <fileId> <path>               Update file, this creates a new revision of the file
gdrive [global] info [options] <fileId>                        Show file info
gdrive [global] mkdir [options] <name>                         Create directory
gdrive [global] share [options] <fileId>                       Share file or directory
gdrive [global] share list <fileId>                            List files permissions
gdrive [global] share revoke <fileId> <permissionId>           Revoke permission
gdrive [global] delete [options] <fileId>                      Delete file or directory
gdrive [global] sync list [options]                            List all syncable directories on drive
gdrive [global] sync content [options] <fileId>                List content of syncable directory
gdrive [global] sync download [options] <fileId> <path>        Sync drive directory to local directory
gdrive [global] sync upload [options] <path> <fileId>          Sync local directory to drive
gdrive [global] changes [options]                              List file changes
gdrive [global] revision list [options] <fileId>               List file revisions
gdrive [global] revision download [options] <fileId> <revId>   Download revision
gdrive [global] revision delete <fileId> <revId>               Delete file revision
gdrive [global] import [options] <path>                        Upload and convert file to a google document, see 'about import' for available conversions
gdrive [global] export [options] <fileId>                      Export a google document
gdrive [global] about [options]                                Google drive metadata, quota usage
gdrive [global] about import                                   Show supported import formats
gdrive [global] about export                                   Show supported export formats
gdrive version                                                 Print application version
gdrive help                                                    Print help
gdrive help <command>                                          Print command help
gdrive help <command> <subcommand>                             Print subcommand help
```

### Synopsis of DriveCommandLine commands

This section provides a brief synopsis of the command line syntax and options
available for the DriveCommandLine commands. Additional info on each command
is available in the
[DriveCommandLine wiki](https://gitlab.com/doctorfree/DriveCommandLine/-/wikis/home).
Each command also has a manual page available via the `man` command by
executing the command:

`man <command-name>`

For example, to view the manual page for the *gdinfo* command, execute:

`man gdinfo`.

All DriveCommandLine commands accept **-c configdir** and **-m maxfiles** arguments:

  -c 'configdir' specifies an alternative gdrive config folder (default: HOME/.gdrive)
  -m 'maxfiles' specifies the maximum number of files in query return
    (default: 1000)

#### Get files
```
gdget [-d] [-f] [-n] [-r] [-s] [-p path] [-o] [-u] path/to/fileorfolder [file2 ...]

options:
  -d                         Indicates delete remote file when download is successful
  -f                         Indicates force overwrite of existing file
  -n                         Indicates tell me what you would do but don't do it
  -o                         Indicates write file content to stdout
  -p 'path'                  Specifies a download path
  -r                         Indicates download directory and its contents recursively
  -s                         Indicates skip existing files
  -u                         Display a usage message and exit
  path/to/fileorfolder       Path of file or folder to get
```

#### File/folder info
```
gdinfo [-i id] [-u] path/to/fileorfolder [file2 ...]

options:
  -u                         Display a usage message and exit
  -i 'id'                    Specifies a Google Drive ID to retrieve for info
  path/to/fileorfolder       Path of file or folder to get info
```

#### List files
```
gdlist [-m maxfiles] [-u] [path/to/folder]

options:
  -m 'maxfiles'              Max files to list, default: 100
  -u                         Display a usage message and exit
  path/to/folder             Path of folder to list. If none provided, list all
```

#### Remove files or folders
```
gdrm [-n] [-r] [-s] [-u] path/to/fileorfolder [file2 ...]

options:
  -n                         Indicates tell me what you would do but don't do it
  -r                         Indicates remove directory and its contents recursively
  -s                         Indicates do not split path to identify name (useful when there is a slash in the filename)
  -u                         Display a usage message and exit
  path/to/fileorfolder       Path of file or folder to remove
```

#### Manage Google Drive share permissionns
```
gdshare [-c configdir] [-m maxfiles] [-r role] [-t type] [-e email] [-d domain] [-D] [-R] [-l] [-n] [-u] path/to/fileorfolder [file2 ...]

options:
  -r 'role' specifies the share role: owner/writer/commenter/reader, default: reader
  -t 'type' specifies the share type: user/group/domain/anyone, default: anyone
  -e 'email' specifies the email address of the user or group to share the file with. Requires 'user' or 'group' as type
  -d 'domain' specifies the name of Google Apps domain. Requires 'domain' as type
  -D indicates make file discoverable by search engines
  -R indicates delete all sharing permissions (owner roles will be skipped)
  -l indicates list files share permissions
  -n indicates tell me what you would do without doing it
  -u displays this usage message
  path/to/fileorfolder     Path of Google Drive file or folder to manage
```

#### Upload files or folders
```
gdupload [-u] path/to/fileorfolder [fileorfolder2 ...]

options:
  -u                         Display a usage message and exit
  path/to/fileorfolder       Path of file or folder to upload
```

#### Retrieve and populate folder IDs
```
getfolderids [-f] [-m maxfiles] [-n] [-u] [-v] [path/to/folder]

options:
  -f                   Indicates 'files', also create a list of file IDs (slower)
  -m 'maxfiles'        Specifies the maximum number of files in query return (default: 500)
  -n                   Indicates tell me what you would do but don't do it
  -v                   Indicates verbose mode
  -u                   Display a usage message and exit
  path/to/folder       Path of folder to populate with Google Drive IDs
```

#### Create/update a Google Drive sync folder
```
sync2drive [-k] [-l] [-m maxfiles] [-n] [-s] [-u] folder|path/to/folder

options:
  -k                   Indicates do not delete extraneous remote files
  -l                   Indicates list sync folders and exit
  -p                   Indicates list sync folders and display path and shared status
  -m 'maxfiles'        Specifies maximum number of file ids to return (default: 100)
  -n                   Indicates tell me what you would do but don't do it
  -s                   Indicates do not split path to identify name (useful when there is a slash in the folder name)
  -u                   Display a usage message and exit
  path/to/folder       Path of folder to sync
```

#### Sync a local folder with a previously created Google Drive sync folder
```
sync_from_drive [-l] [-n] [-u] folder | path/to/folder

options:
  -n                   Indicates tell me what you would do but don't do it
  -l                   Indicates list sync folders and exit
  -u                   Display a usage message and exit
  path/to/folder       Path of file or folder to upload
```

### Examples
#### Retrieve and populate local folders with Google Drive IDs
`getfolderids MagicMirror`

Retrieve and populate folder IDs in the 'MagicMirror' folder and all subfolders within

#### Get files
`gdget README`

Downloads top-level Google Drive file `README`

`gdget -o README | grep AUTHOR`

Downloads top-level Google Drive file `README` to stdout and pipes that to the `grep` utility

`gdget foo/bar`

Downloads Google Drive folder `bar` located in folder `foo` and downloads all its contents recursively

`gdget foo/bar/spam`

Downloads Google Drive file `spam` located in folder `foo/bar`

`gdget -p tmp foo/bar/spam`

Downloads Google Drive file `spam` located in Google Drive folder `foo/bar` to local folder 'tmp'

#### Get file or folder info
`gdinfo README`

Displays information for the top-level Google Drive file `README`

`gdinfo foo/bar/spam`

Displays information for the Google Drive file `spam` located in folder `foo/bar`

#### List files
`gdlist`

Lists all Google Drive files and folders up to the default maximum number

`gdlist -m 1000`

Lists up to 1000 Google Drive files and folders

`gdlist MagicMirror`

Lists the Google Drive files and folders in the 'MagicMirror' folder

#### Remove Google Drive files or folders
`gdrm README`

Removes top-level Google Drive file `README`

`gdrm foo/bar/spam`

Removes Google Drive file `spam` located in folder `foo/bar`

`gdrm -r foo/bar/spam`

Removes Google Drive folder `spam` located in folder `foo/bar` and removes all its contents recursively

#### Upload files and folders to Google Drive
`gdupload README`

Uploads local file `README` to top-level Google Drive folder

`gdupload foo/bar/spam`

Uploads local file `spam` located in folder `foo/bar` to Google Drive folder `foo/bar`

`gdupload foo/bar/spam`

Uploads local folder `spam` located in folder `foo/bar` and uploads all its contents recursively

#### Create/update Google Drive sync folder

`sync2drive MagicMirror`

Syncs the local folder `MagicMirror` and its contents to the Google Drive folder `MagicMirror`

`sync2drive MagicMirror/config`

Syncs the local folder `MagicMirror/config` and its contents to the Google Drive folder `MagicMirror/config`

#### Sync local folder to Google Drive sync folder

`sync_from_drive MagicMirror`

Syncs the local folder `MagicMirror` and its contents to the Google Drive folder `MagicMirror`

`sync_from_drive MagicMirror/config`

Syncs the local folder `MagicMirror/config` and its contents to the Google Drive folder `MagicMirror/config`

## Example application

A software distribution or packaged application may need to download files during
or after the initial installation. For example, a Debian format package install
might run a `postinst` script that downloads files the package requires from
Google Drive rather than including these files in the installation package.

Google Drive files and folders can be programmatically downloaded in a variety
of ways. For example, the Python/Pip `gdown` utility can be used to download
Google Drive files. However, automated Google Drive downloads require the
Google Drive IDs of any files or folders to be downloaded in this manner.

The DriveCommandLine package can be used to fetch these IDs. The workflow might
look something like the following.

Sync a local folder containing the files needed for download to a Google Drive:

`sync2drive Applications/Downloads`

Retrieve file and folder IDs in the Google Drive `Applications/Downloads` folder:

`getfolderids -f Applications/Downloads`

Edit the resulting list of IDs in the locally generated drive_ids file:

`vi drive_ids/Applications_Downloads_file_ids.txt`

Add the list of file and/or folder IDs needed for download to the `postinst` script.

## Limitations

### Managing the same Google Drive from multiple computers

The DriveCommandLine utilities manage Google Drives by maintaining a mirror
of the Google Drive folders and their IDs. When DriveCommandLine commands
are executed they often need to update these locally stored folder IDs.

In situations where multiple computers are being used to manage the same
Google Drive with DriveCommandLine, one system may update its locally
stored folder IDs while other systems will remain in an unupdated state.

Updating multiple systems running DriveCommandLine to manage the same
Google Drive must be done manually. This can be accomplished by running
the `getfolderids` command on each system that needs to be updated.

### Spaces in file and folder names

A significant effort has been made to accomodate file and folder names that
contain spaces. However, there may still be code paths that do no properly
handle spaces in file or folder names. The whole issue of spaces
in file and folder names arose as a result of Microsoft deciding to enable
that feature and we have been struggling for the last quarter century to
accomodate their decision. We should have just said no.

Google Drive is frequently used to store files and folders imported from
Microsoft Windows platforms. Therefore, spaces in files and folders is an
important feature to support. The latest testing of DriveCommandLine
indicates that spaces in file and folder names works as expected.

Our recommendation is to avoid spaces in files and folder names but if you
do see any problem with these utilities managing such files or folders, please
raise an issue at https://gitlab.com/doctorfree/DriveCommandLine/-/issues

## Troubleshooting

Most problems with DriveCommandLine arise from mismatched or stale folder IDs
stored locally. If you run into an issue the first thing to try is resync
folder IDs by executing the `getfolderids` command. Rerun the command that
previously exhibited an issue after syncing folder IDs.

Another area that can be problematic is the management of multiple Google
Drives. The DriveCommandLine utilities all accept a `-c configdir` option
to specify which Google Drive to manage. Problems can arise when the
configuration folder is not specified or is specified incorrectly.

Except for the `gdrive` binary, all the DriveCommandLine commands are
Bash scripts. To see what these scripts are executing when they run,
execute the command with `bash -x ...`. For example, to view the execution
of `gdget`, invoke it as `bash -x gdget ...`.

Please report unresolved issues with DriveCommandLine by raising an issue
at https://gitlab.com/doctorfree/DriveCommandLine/-/issues

## Compile from source

If you want to [compile from source](#compile-from-source) you need the
[go toolchain](http://golang.org/doc/install) version 1.5 or higher.

To compile the `gdrive` binary and install it locally, issue the command:

```bash
go install github.com/prasmussen/gdrive@latest
```

The gdrive binary should now be available at `$GOPATH/bin/gdrive`

If you want to create your own custom DriveCommandLine package then you
need the appropriate packaging tools installed on your system.

For the creation of Debian format installable packages the `build-essential`
package is required and the `devscripts` package is useful for maintainers.

For the creation of RPM format installable packages several packages are
required/useful.

On Fedora, CentOS 8, and RHEL 8:

```bash
dnf install gcc rpm-build rpm-devel rpmlint make python bash coreutils diffutils patch rpmdevtools
```

On CentOS 7 and RHEL 7:

```bash
yum install gcc rpm-build rpm-devel rpmlint make python bash coreutils diffutils patch rpmdevtools
```

Once you have the appropriate development environment installed you can create
DriveCommandLine packages by cloning the repository and running `mkpkg`:

```bash
git clone https://gitlab.com/doctorfree/DriveCommandLine.git
cd DriveCommandLine
./mkpkg
```

The DriveCommandLine package can then be installed by executing the `Install` command:

```bash
./Install
```

and, similarly, removed by executing the `Uninstall` command.

### Cool feature used by this repository

I am a GO fanboy but I was unaware of the ease with which GO builds and installs
can be performed and integrated into a repository's continuous integration.

The DriveCommandLine packages include the `gdrive` command line control of Google
Drive. This is a GO binary. Rather than fork or clone the entire `gdrive`
repository, this repository's CI build of DriveCommandLine packages employs
the remote build and installation of `gdrive` by the simple invocation of the
command:

`go install github.com/prasmussen/gdrive@latest`

during package creation. That is, I am able to build and install from a remote
repository during this repository's packaging process. I thought that was
pretty cool.

## Removal

### Debian based Linux removal

On Debian based Linux systems where the DriveCommandLine package was installed
using the DriveCommandLine Debian format package, remove the DriveCommandLine
package by executing the command:

```bash
    sudo apt remove drivecommandline
```
or
```bash
    sudo dpkg -r drivecommandline
```

**Note:** Removal may issue a warning about removing `/usr/local` and other
folders within `/usr/local`. This is an artifact of the Debian packaging system.
If you wish to silence that warning and prevent the Debian packaging system from
trying to remove `/usr/local` then install the
[core-custom-local Debian package](https://gitlab.com/doctorfree/core-custom-local/-/releases).

### RPM based Linux removal

On RPM based Linux systems where the DriveCommandLine package was installed
using the DriveCommandLine RPM format package, remove the DriveCommandLine
package by executing the command:

```bash
    sudo yum remove DriveCommandLine
```
or
```bash
    sudo rpm -e DriveCommandLine
```

### Manual removal

On all other systems where the DriveCommandLine package was installed manually,
remove the DriveCommandLine package by executing the `scripts/manual_uninstall.sh`
in the DriveCommandLine source repository. This script performs the following:

```bash
#!/bin/bash

BINS="sync2drive \
      getfolderids \
      gdinfo \
      gdlist \
      gdrive \
      gdupload \
      gdget \
      gdrm \
      sync_from_drive"

MANS="gdupload.1 \
      gdrm.1 \
      sync2drive.1 \
      gdget.1 \
      getfolderids.1 \
      sync_from_drive.1 \
      gdinfo.1 \
      gdlist.1 \
      gdrive.1"

DOCS="DriveCommandLine"

[ -d /usr/local/bin ] && {
    cd /usr/local/bin
    sudo rm -f ${BINS}
}
[ -d /usr/local/share/man/man1 ] && {
    cd /usr/local/share/man/man1
    sudo rm -f ${MANS}
}
[ -d /usr/local/share/doc ] && {
    cd /usr/local/share/doc
    sudo rm -rf ${DOCS}
}

echo "DriveCommandLine installation files and folders removed"
exit 0
```

## See also

- [Asciiville](Asciiville.md)
- [MagicMirror](MagicMirror.md)
- [MirrorCommand](MirrorCommand.md)
- [MusicPlayerPlus](MusicPlayerPlus.md)
- [RoonCommandLine](RoonCommandLine.md)
