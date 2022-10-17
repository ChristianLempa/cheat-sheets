# Ronnie's "Cheat-Sheets"

This repository contains cheat sheets, project information, documentation, code snippets, and other information in Markdown format. The main feature of this repository of markdown files is that the files have been manicured to contain internal backlinks thus exposing their inter-relationships. It's a knowledge base with metadata providing insight.

## Obsidian plus NB

The open source [command line tool nb](https://github.com/xwmx/nb) is another
powerful knowledge base application. [Obsidian](https://obsidian.md/) and nb
can be used together to provide an even more powerful, rich, flexible,
cross-platform knowledge base. In addition to note-taking, nb provides features
like bookmarking, archiving, encryption, filtering, format conversion, todos
with tasks, and more.

Both nb and Obsidian utilize plain text data storage in Markdown format.
Both sync across platforms with `git`. They complement one another and work
well together.

These markdown files are intended to be used with [[nb]] and
[[obsidian|Obsidian]]. For example, to create an nb notebook
from an existing Obsidian vault (or any repository with markdown):

```
nb notebooks add cheat-sheets https://github.com/doctorfree/cheat-sheets.git
```

This would create an nb notebook named 'cheat-sheets'. The 'cheat-sheets' nb
notebook is just a clone of the specified Github repository. If that repository
were an Obsidian vault then changes/updates to the Obsidian vault can now be
made in either Obsidian or nb. All changes will automatically sync and be
available across all platforms where either Obsidian or nb is deployed.

## Obsidian license restriction

Obsidian is free for personal use. However, the license includes a restriction
on the use of Obsidian for revenue generating activities. Here is the relevant
section from the Obsidian license:

```
You need to pay for Obsidian if and only if you use it to contribute, directly
or indirectly, to revenue-generating, work-related activities in a company that
has two or more people.
```

The `nb` note-taking command line application has no such restriction and is
completely free and open source software licensed under the GNU Affero General
Public License v3.0.

## History

The starting point for this repository was the **Cheat-Sheets** repository maintained by Christian Lempa at
[https://github.com/xcad2k/cheat-sheets](https://github.com/xcad2k/cheat-sheets).

Christian has created detailed, in-depth tutorials on some tools or technologies on his YouTube Channel: [The Digital Life](https://www.youtube.com/channel/UCZNhwA1B5YqiY1nLzmM0ZRg).

## Other Resources

- [Asciiville](https://github.com/doctorfree/Asciiville) - Ascii Art, text based utilities, tools, games, fun
- [DriveCommandLine](https://github.com/doctorfree/DriveCommandLine) - Initialize, configure, monitor, and manage Google Drives from the command line
- [MirrorCommand](https://github.com/doctorfree/MirrorCommand) - Initialize, configure, monitor, and manage a MagicMirror from the command line
- [MusicPlayerPlus](https://github.com/doctorfree/MusicPlayerPlus) - Services, tools, clients for self hosting and managing a music library
- [RoonCommandLine](https://github.com/doctorfree/RoonCommandLine) - Command line control of the Roon audio system over a local network
- [dotfiles-ubuntu](https://github.com/doctorfree/dotfiles-ubuntu) - My personal configuration files for Linux
- [dotfiles-macos](https://github.com/doctorfree/dotfiles-macos) - My personal configuration files for Mac OS

## Support me

Sponsor my projects at
[https://github.com/sponsors/doctorfree](https://github.com/sponsors/doctorfree)

***Help me to create something that matters to people!***
