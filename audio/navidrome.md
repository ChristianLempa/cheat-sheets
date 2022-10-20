---
tags:
    - audio
    - server
    - mpplus
categories:
    - audio
---

<a href="https://www.navidrome.org"><img src="https://raw.githubusercontent.com/navidrome/navidrome/master/resources/logo-192x192.png" alt="Navidrome logo" title="navidrome" align="right" height="60px" /></a>

# Navidrome Music Server

| Last Release            | Build                   | Downloads         | Docker       |
|-------------------------|-------------------------|-------------------|--------------|
| [![Last Release](https://img.shields.io/github/v/release/navidrome/navidrome?logo=github&label=latest&style=flat-square)](https://github.com/navidrome/navidrome/releases) | [![Build](https://img.shields.io/github/workflow/status/navidrome/navidrome/Build?logo=github&style=flat-square)](https://nightly.link/navidrome/navidrome/workflows/pipeline/master) | [![Downloads](https://img.shields.io/github/downloads/navidrome/navidrome/total?logo=github&style=flat-square)](https://github.com/navidrome/navidrome/releases/latest) | [![Docker Pulls](https://img.shields.io/docker/pulls/deluan/navidrome?logo=docker&label=pulls&style=flat-square)](https://hub.docker.com/r/deluan/navidrome) |

| Dev Chat                | Subreddit               | Contributor Covenant |
|-------------------------|-------------------------|----------------------|
| [![Dev Chat](https://img.shields.io/discord/671335427726114836?logo=discord&label=discord&style=flat-square)](https://discord.gg/xh7j7yF) | [![Subreddit](https://img.shields.io/reddit/subreddit-subscribers/navidrome?logo=reddit&label=/r/navidrome&style=flat-square)](https://www.reddit.com/r/navidrome/) | [![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0-ff69b4.svg?style=flat-square)](CODE_OF_CONDUCT.md) |

## [Check out our Live Demo!](https://www.navidrome.org/demo/)

Navidrome is an open source web-based music collection server and streamer. It gives you freedom to listen to your music collection from any browser or mobile device. It's like your personal Spotify!

An automated installation and configuration of ***Navidrome*** is included in [MusicPlayerPlus](../projects/MusicPlayerPlus.md).

__Any feedback is welcome!__ If you need/want a new feature, find a bug or think of any way to improve Navidrome, 
please file a [GitHub issue](https://github.com/navidrome/navidrome/issues) or join the discussion in our 
[Subreddit](https://www.reddit.com/r/navidrome/). If you want to contribute to the project in any other way 
([ui/backend dev](https://www.navidrome.org/docs/developers/), 
[translations](https://www.navidrome.org/docs/developers/translations/), 
[themes](https://www.navidrome.org/docs/developers/creating-themes)), please join the chat in our 
[Discord server](https://discord.gg/xh7j7yF). 

## Installation

See instructions in the [project's website](https://www.navidrome.org/docs/installation/)

If you plan to host Navidrome in the cloud, a great option is to get a virtual server at [BuyVM](https://my.frantech.ca/aff.php?aff=4605). 
They have plans that start at $3.50/month! If you decide to sign up, please consider using our [affliliate link](https://my.frantech.ca/aff.php?aff=4605),
to help support the project <3

## Features
 
 - Handles very **large music collections**
 - Streams virtually **any audio format** available
 - Reads and uses all your beautifully curated **metadata**
 - Great support for **compilations** (Various Artists albums) and **box sets** (multi-disc albums)
 - **Multi-user**, each user has their own play counts, playlists, favourites, etc...
 - Very **low resource usage**
 - **Multi-platform**, runs on macOS, Linux and Windows. **Docker** images are also provided
 - Ready to use binaries for all major platforms, including **Raspberry Pi**
 - Automatically **monitors your library** for changes, importing new files and reloading new metadata 
 - **Themeable**, modern and responsive **Web interface** based on [Material UI](https://material-ui.com)
 - **Compatible** with all Subsonic/Madsonic/Airsonic [clients](https://www.navidrome.org/docs/overview/#apps)
 - **Transcoding** on the fly. Can be set per user/player. **Opus encoding is supported**
 - Translated to **various languages**

## Documentation
All documentation can be found in the project's website: https://www.navidrome.org/docs. 
Here are some useful direct links:

- [Overview](https://www.navidrome.org/docs/overview/)
- [Installation](https://www.navidrome.org/docs/installation/)
  - [Docker](https://www.navidrome.org/docs/installation/docker/)
  - [Binaries](https://www.navidrome.org/docs/installation/pre-built-binaries/)
  - [Build from source](https://www.navidrome.org/docs/installation/build-from-source/)
- [Development](https://www.navidrome.org/docs/developers/)
- [Subsonic API Compatibility](https://www.navidrome.org/docs/developers/subsonic-api/)

## Screenshots

<p align="left">
    <img height="550" src="https://raw.githubusercontent.com/navidrome/navidrome/master/.github/screenshots/ss-mobile-login.png">
    <img height="550" src="https://raw.githubusercontent.com/navidrome/navidrome/master/.github/screenshots/ss-mobile-player.png">
    <img height="550" src="https://raw.githubusercontent.com/navidrome/navidrome/master/.github/screenshots/ss-mobile-album-view.png">
    <img width="550" src="https://raw.githubusercontent.com/navidrome/navidrome/master/.github/screenshots/ss-desktop-player.png">
</p>

## See also

- [Mopidy](mopidy.md)
- [MusicPlayerPlus](../projects/MusicPlayerPlus.md)
