# [Irssi](https://irssi.org)

***Irssi*** is a modular text mode chat client. It comes with IRC support built in, and there are third party [ICB](https://github.com/jperkin/irssi-icb), [SILC](http://www.silcnet.org/), [XMPP](http://cybione.org/~irssi-xmpp/) (Jabber), [PSYC](http://about.psyc.eu/Irssyc) and [Quassel](https://github.com/phhusson/quassel-irssi) protocol modules available.

![irssi](https://user-images.githubusercontent.com/5665186/32180643-cf127f60-bd92-11e7-8aa2-882313ce1d8e.png)

## Installation

### Ubuntu

```bash
    apt-get install irssi
```

### Debian

```bash
    apt-get install irssi
```

### Alpine

```bash
    apk add irssi
```

### Arch Linux

```bash
    pacman -S irssi
```

### Kali Linux

```bash
    apt-get install irssi
```

### CentOS

```bash
    yum install irssi
```

### Fedora

```bash
    dnf install irssi
```

### Windows (WSL2)

```bash
    sudo apt-get update sudo apt-get install irssi
```

### OS X

```bash
    brew install irssi
```

### Raspbian

```bash
    apt-get install irssi
```

### Dockerfile

```bash
    dockerfile.run/irssi
```

### Docker

```bash
    docker run cmd.cat/irssi irssi
```

## [Source and build information](https://irssi.org/download/)

### Development source installation

[Ninja](https://ninja-build.org/) 1.8 and [Meson](https://mesonbuild.com/) 0.53

```
git clone https://github.com/irssi/irssi
cd irssi
meson Build
ninja -C Build && sudo ninja -C Build install
```

### Release source installation

* Download [release](https://github.com/irssi/irssi/releases)
* Verify signature
```
tar xJf irssi-*.tar.xz
cd irssi-*
meson Build
ninja -C Build && sudo ninja -C Build install
```

### Requirements

- [glib-2.32](https://wiki.gnome.org/Projects/GLib) or greater
- [openssl](https://www.openssl.org/)
- [perl-5.6](https://www.perl.org/) or greater (for perl support)
- terminfo or ncurses (for text frontend)

#### See the [INSTALL](https://github.com/irssi/irssi/blob/master/INSTALL) file for details

## [Documentation](https://irssi.org/documentation/)

* [New users guide](https://irssi.org/New-users/)
* [Questions and Answers](https://irssi.org/documentation/qna/)
* Check the built-in `/HELP`, it has all the details on command syntax

## [Themes](https://irssi-import.github.io/themes/)

## [Scripts](https://scripts.irssi.org/)

## [Modules](https://irssi.org/modules/)

## [Security information](https://irssi.org/security/)

Please report security issues to staff@irssi.org. Thanks!

## [Bugs](https://github.com/irssi/irssi/issues) / Suggestions / Contributing

Check the GitHub issues if it is already listed in there; if not, open an issue on GitHub or send a mail to [staff@irssi.org](mailto:staff@irssi.org).

You can also contact the Irssi developers in [#irssi](https://irssi.org/support/irc/) on irc.libera.chat.

## See also

- [Asciiville](../projects/Asciiville.md)
- [Tuir](tuir/tuir.md)
- [Neomutt](neomutt.md)
- [Newsboat](newsboat.md)
