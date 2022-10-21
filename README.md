# Collaborative Cheat Sheets

Hi, there! 👋

This repository contains cheat sheets, project information, documentation, code snippets, and other useful information. The main feature of this knowledge base repository is that the markdown files have been manicured to contain internal backlinks and tags thus exposing their inter-relationships. It's a knowledge base with metadata providing insight.

This knowledge base has been developed through the efforts of several individuals. It is licensed under the [MIT open source license](LICENSE) and can be shared freely as long as the individual copyrights are retained. Please feel free to contribute with additional cheat sheets and documentation, corrections, suggestions, enhancements, or simply buy us a cup of coffee.

## Table of Contents

1. [Authors](#authors)
1. [Why](#why)
1. [Usage](#usage)
    1. [Markdown viewers](#markdown-viewers)
    1. [Clone and view locally](#clone-and-view-locally)
    1. [Obsidian plus NB](#obsidian-plus-nb)
    1. [Obsidian license restriction](#obsidian-license-restriction)
1. [Auto Cheat Sheets](#auto-cheat-sheets)
1. [Resources](#resources)
1. [Support](#support)

## Authors

[Doctorfree](https://github.com/doctorfree), the online handle used by [Ronald Record](https://ronrecord.com), is an aging rogue hippie whose open source contributions extend back to the early 80s sharing computational applications of dynamical systems theory on [Usenet](https://en.wikipedia.org/wiki/Usenet). Record created and maintained the popular [Skunkware](https://en.wikipedia.org/wiki/SCO_Skunkware) repository of open source throughout the 90s and 2000s. He was a founding member of [86open](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format#86open) and co-inventor of the [Web desktop](https://en.wikipedia.org/wiki/Web_desktop).

[Christian Lempa](https://github.com/ChristianLempa) is a 35 year-old tech enthusiast from Germany who loves to inspire and educate people in IT.  He created cheat sheets and documentation at [https://github.com/ChristianLempa/cheat-sheets](https://github.com/ChristianLempa/cheat-sheets) as free resources to be used in specific use cases. If you're searching for detailed, in-depth tutorials on some tools or technologies, check out his YouTube Channel: [The Digital Life](https://www.youtube.com/@christianlempa).

Several of the cheat sheets included here are adapted from the excellent library of cheat sheets created and maintained by Randy at [QuickRef.ME](https://quickref.me) (also released under the MIT license). Randy doesn't even know he contributed to this repository but his use of an open source license enabled effortless collaboration.

## Why

You may ask yourself, "Why does this repository even exist? What good is it?". Yes, there are many "cheat-sheet" repositories, some of them quite mature. What is the purpose of yet another cheatsheet repo? We believe this repository provides additional value in several ways detailed below.

### CommonMark specification conformance

First, some history. For a thorough read, visit the [CommonMark website](https://commonmark.org).

Quoting from the CommonMark spec's introduction:

> Markdown is a plain text format for writing structured documents, based on conventions for indicating formatting in email and usenet posts.  It was developed by John Gruber (with help from Aaron Swartz) and released in 2004 in the form of a [syntax description](http://daringfireball.net/projects/markdown/syntax) and a Perl script (`Markdown.pl`) for converting Markdown to HTML.  In the next decade, dozens of implementations were developed in many languages.  Some extended the original Markdown syntax with conventions for footnotes, tables, and other document elements.  Some allowed Markdown documents to be rendered in formats other than HTML.  Websites like Reddit, StackOverflow, and GitHub had millions of people using Markdown.  And Markdown started to be used beyond the web, to author books, articles, slide shows, letters, and lecture notes.
>
> ... 
>
> Because there is no unambiguous spec, implementations have diverged considerably. As a result, users are often surprised to find that a document that renders one way on one system (say, a GitHub wiki) renders differently on another (say, converting to docbook using pandoc). To make matters worse, because nothing in Markdown counts as a "syntax error", the divergence often isn't discovered right away.

Authors of markdown documents often write and test their markdown only to verify that it displays correctly in the system they are using. For example, many authors using Github only verify their markdown on Github using a browser. Github flavored markdown contains many extensions that are not supported in other markdown systems. Markdown written to conform with a particular extension or flavor is not portable and when other viewers or systems attempt to display such markdown it can fail in a variety of ways.

To overcome this problem, the CommonMark markdown specification was written and it has been widely adopted. This repository utilizes markdown for all of the cheat sheets and every effort has been made to conform with the [CommonMark Spec](https://spec.commonmark.org). As such, these cheat sheets are not only portable but can be viewed by any markdown editor/viewer that conforms to that specification.

### Tags

[Markdown](text/markdown.md) supports the inclusion of tags in a [YAML](text/yaml.md) prelude. Our cheat sheets utilize tags extensively in an attempt to enhance the inter-relationships and qualitative properties of each. Some markdown viewers, like Obsidian, can take advantage of tags to highlight aspects and relationships between elements in a collection.

Tags are an important but often overlooked feature in note-taking and personal knowledge management systems. For example, the [Zettelkasten](https://en.wikipedia.org/wiki/Zettelkasten) method can be enhanced greatly through the use of tags. Too often knowledge management systems utilize categories rather than tags, ignoring the fact that many elements have cross-category relationships.

### Backlinks

Quite a bit of effort has gone into creating internal links between these cheatsheets. These are referred to as *[Backlinks](https://en.wikipedia.org/wiki/Backlink)* in some systems. The incorporation of backlinks enables a "What links here" capability that can be exploited by viewers.

### Wikipedia style introductory matter

In addition to providing a quick overview of usage, these cheatsheets often include a prefatory explanation of the subject, its history, origin, evolution, and use. Often times this is just the opening paragraph of the corresponding Wikipedia article. Our cheatsheets provide a context in which to view the subject.

### Use of HTML Character Entities

It's somewhat shocking how often HTML and Markdown authors ignore the often necessary use of HTML character entitities in their documents. In many representations some characters can be mistakenly recognized as delimiters or other formatting constructs rather than the intended symbol. For example, in a table the delimiting character between fields is the pipe symbol '|'. When this symbol is used inside a table field it can be mistakenly recognized as representing the end of that field. This can be particularly important when describing things like the syntax of a [regular expression](linux/regex.md) or a series of pipes in a [shell command](linux/shell-commands.md).

This will not display as intended:

```
| Description                 | Command         |
|-----------------------------|-----------------|
| Number of files in a folder | `ls -l | wc -l` |
```

Displays as:

| Description                 | Command         |
|-----------------------------|-----------------|
| Number of files in a folder | `ls -l | wc -l` |

In this example, use the HTML character entity for the pipe symbol inside the 'code' tag:

```
| Description                 | Command                         |
|-----------------------------|---------------------------------|
| Number of files in a folder | <code>ls -l &#124; wc -l</code> |
```

Displays as:

| Description                 | Command                         |
|-----------------------------|---------------------------------|
| Number of files in a folder | <code>ls -l &#124; wc -l</code> |

Our cheatsheets have been meticulously groomed to avoid these kinds of errors through the appropriate use of HTML character entities.

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

## Auto Cheat Sheets

Resources exist on the web and as command line clients to auto-generate cheat sheets.

For example, to display the cheat sheet for the `wget` command, visit the URL [https://cheat.sh/wget](https://cheat.sh/wget). Use a similar URL for just about any common Unix/Linux command.

Another way to use this same service from the command line is with `curl`. For example, to retrieve the cheat sheet for the `ls` command from the command line:

```bash
curl cheat.sh/ls
```

## Resources

- [John Gruber's Markdown Project](https://daringfireball.net/projects/markdown) - The co-inventor of the Markdown markup language hosts an excellent resource on Markdown
- [CommonMark Markdown Spec](https://spec.commonmark.org) - John MacFarlane hosts this specification and interactive dingus for Markdown
- MIT Licensed Cheat Sheet Repos
    - [https://github.com/chubin/cheat.sheets](https://github.com/chubin/cheat.sheets) - Repository of the *[cheat.sh](https://cheat.sh/)* 
    - [https://github.com/kasramp/cheat-sheet-factory](https://github.com/kasramp/cheat-sheet-factory) - Cheat Sheet Factory
    - [https://github.com/Randy8080/reference](https://github.com/Randy8080/reference) - Quickref.ME cheat sheets
    - [Christian's Cheat-Sheets](https://github.com/christianlempa/cheat-sheets) - Command Reference for various tools and technologies
- [Videos](https://github.com/christianlempa/videos) - Documentation and project files for Christian's video tutorials on YouTube
- [dotfiles-ubuntu](https://github.com/doctorfree/dotfiles-ubuntu) - Doctorfree's personal configuration files for Linux
- [dotfiles-macos](https://github.com/doctorfree/dotfiles-macos) - Doctorfree's personal configuration files for Mac OS
- [Dotfiles](https://github.com/christianlempa/dotfiles) - Christian's personal configuration files on Linux and Windows
- [Boilerplates](https://github.com/christianlempa/boilerplates) - Templates for various projects like Docker, K8S, Ansible, etc
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

