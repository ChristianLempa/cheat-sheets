# Collaborative Cheat Sheets

Hi, there! 👋

This repository contains cheat sheets, project information, documentation, code snippets, and other useful information. The main feature of this knowledge base repository is that the markdown files have been manicured to contain internal backlinks and tags thus exposing their inter-relationships. It's a knowledge base with metadata providing insight.

This knowledge base has been developed through the efforts of several individuals. It is licensed under the [MIT open source license](LICENSE) and can be shared freely as long as the individual copyrights are retained. Please feel free to contribute with additional cheat sheets and documentation, corrections, suggestions, enhancements, or simply buy us a cup of coffee.

## Table of Contents

1. [Authors](#authors)
1. [Usage](#usage)
    1. [Markdown viewers](#markdown-viewers)
    1. [Clone and view locally](#clone-and-view-locally)
    1. [Obsidian plus NB](#obsidian-plus-nb)
    1. [Obsidian license restriction](#obsidian-license-restriction)
1. [Resources](#resources)
1. [Support](#support)

## Authors

[Doctorfree](https://github.com/doctorfree), the online handle used by [Ronald Record](https://ronrecord.com), is an aging rogue hippie whose open source contributions extend back to the early 80s sharing computational applications of dynamical systems theory on [Usenet](https://en.wikipedia.org/wiki/Usenet). Record created and maintained the popular [Skunkware](https://en.wikipedia.org/wiki/SCO_Skunkware) repository of open source throughout the 90s and 2000s. He was a founding member of [86open](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format#86open) and co-inventor of the [Web desktop](https://en.wikipedia.org/wiki/Web_desktop).

[Christian Lempa](https://github.com/xcad2k) is a 35 year-old tech enthusiast from Germany who loves to inspire and educate people in IT.  He created cheat sheets and documentation at [https://github.com/xcad2k/cheat-sheets](https://github.com/xcad2k/cheat-sheets) as free resources to be used in specific use cases. If you're searching for detailed, in-depth tutorials on some tools or technologies, check out his YouTube Channel: [The Digital Life](https://www.youtube.com/channel/UCZNhwA1B5YqiY1nLzmM0ZRg).

Several of the cheat sheets included here are adapted from the excellent library of cheat sheets created and maintained by Randy at [QuickRef.ME](https://quickref.me) (also released under the MIT license). Randy doesn't even know he contributed to this repository but his use of an open source license enabled effortless collaboration.

## Usage

Any [markdown](https://en.wikipedia.org/wiki/Markdown) viewer can be used to view this knowledge base. You can simply browse the repository and click on the individual markdown files at https://github.com/doctorfree/cheat-sheets.git in any web browser. However, to view the inter-relationships between the many components, categories, and technologies documented here, we recommend using the [Obsidian](https://obsidian.md) knowledge base engine. Obsidian is free for personal non-commercial use but must be purchased in revenue generating operations (see the note on [Obsidian license restrictions](#obsidian-license-restriction) below).

### Markdown viewers

Recommended markdown viewers, available for all platforms and with many features:

- [Obsidian](https://obsidian.md)
- [nb](https://xwmx.github.io/nb)

If Obsidian does not suit your needs, there are many free an open source markdown editors and viewers available for all platforms. Doctorfree uses the [nb](https://xwmx.github.io/nb/) command line and local web note-taking, bookmarking, archiving, and knowledge base application. Obsidian and nb work well together to provide a rich markdown editing, viewing, and management system. See the [Obsidian plus NB](#obsidian-plus-nb) section below for details.

Several excellent resources exist that provide lists and reviews of popular markdown editors and viewers:

- https://github.com/rhythmus/markdown-resources
- https://github.com/mundimark/awesome-markdown-editors
- http://mac.appstorm.net/tag/markdown
- http://mashable.com/2013/06/24/markdown-tools
- http://pastebin.com/j7Pjq1QT
- http://brettterpstra.com/ios-text-editors

Obsidian is pretty cool though, so try it out.

### Clone and view locally

To explore this repository locally or to integrate it into a service, first clone the repository:

```
git clone https://github.com/doctorfree/cheat-sheets.git
```

This will result in a local folder, `cheat-sheets`, containing all of the markdown and supporting file assets. Import these into your markdown viewer. The import method varies from viewer to viewer. To import into Obsidian:

- Open another vault (or create new vault if first time)
- Open folder as vault (click "Open")
- Navigate to the `cheat-sheets` folder created by `git clone ...`
- Click "Open" to create the new Obsidian vault

### Obsidian plus NB

The open source [command line tool nb](https://github.com/xwmx/nb) is another
powerful knowledge base application. [Obsidian](https://obsidian.md/) and nb
can be used together to provide an even more powerful, rich, flexible,
cross-platform knowledge base. In addition to note-taking, nb provides features
like bookmarking, archiving, encryption, filtering, format conversion, todos
with tasks, and more.

Both nb and Obsidian utilize plain text data storage in Markdown format.
Both sync across platforms with `git`. They complement one another and work
well together.

These markdown files are intended to be used with [NB](text/nb) and
[Obsidian](text/obsidian). For example, to create an nb notebook
from an existing Obsidian vault (or any repository with markdown):

```
nb notebooks add cheat-sheets https://github.com/doctorfree/cheat-sheets.git
```

This would create an nb notebook named 'cheat-sheets'. The 'cheat-sheets' nb
notebook is just a clone of the specified Github repository. If that repository
were an Obsidian vault then changes/updates to the Obsidian vault can now be
made in either Obsidian or nb. All changes will automatically sync and be
available across all platforms where either Obsidian or nb is deployed.

### Obsidian license restriction

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

## Resources

- [Videos](https://github.com/xcad2k/videos) - Documentation and project files for Christian's video tutorials on YouTube
- [dotfiles-ubuntu](https://github.com/doctorfree/dotfiles-ubuntu) - Doctorfree's personal configuration files for Linux
- [dotfiles-macos](https://github.com/doctorfree/dotfiles-macos) - Doctorfree's personal configuration files for Mac OS
- [Dotfiles](https://github.com/xcad2k/dotfiles) - Christian's personal configuration files on Linux and Windows
- [Boilerplates](https://github.com/xcad2k/boilerplates) - Templates for various projects like Docker, K8S, Ansible, etc
- [Christian's Cheat-Sheets](https://github.com/xcad2k/cheat-sheets) - Command Reference for various tools and technologies
- Doctorfree Projects
  - [Asciiville](https://github.com/doctorfree/Asciiville) - Ascii Art, text based utilities, tools, games, fun
  - [DriveCommandLine](https://github.com/doctorfree/DriveCommandLine) - Initialize, configure, monitor, and manage Google Drives from the command line
  - [MirrorCommand](https://github.com/doctorfree/MirrorCommand) - Initialize, configure, monitor, and manage a MagicMirror from the command line
  - [MusicPlayerPlus](https://github.com/doctorfree/MusicPlayerPlus) - Services, tools, clients for self hosting and managing a music library
  - [RoonCommandLine](https://github.com/doctorfree/RoonCommandLine) - Command line control of the Roon audio system over a local network

## Support

Support our mission to create free, high-quality content for tech enthusiasts and IT professionals:

- [Sponsor the projects of Doctorfree](https://github.com/sponsors/doctorfree)
- [Become a Patreon of Christian](https://www.patreon.com/christianlempa)
- [Buy Randy a cup of coffee](https://buymeacoffee.com/randy8080)

***Help us to create something that matters to people!***

