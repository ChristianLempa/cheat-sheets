# Flatpak

Flatpak, formerly known as xdg-app, is a utility for software deployment and package management for [Linux](linux.md). It is advertised as offering a sandbox environment in which users can run application software in isolation from the rest of the system.

Flathub, a repository (or remote source in the Flatpak terminology) located at flathub.org, has become the de facto standard for getting applications packaged with Flatpak. Packages are added to it by both the Flathub administrators and the developers of the programs themselves (though the admins have stated their preference for developer-submitted apps). Although Flathub is the de facto source for applications packaged with Flatpak, it is possible to host a Flatpak repository that is independent of Flathub.

Flatpak apps can be installed on any existing Linux distribution including those installed with the Windows Subsystem for Linux compatibility layer.

## Installation and setup

See https://flatpak.org/setup/ for installation and setup steps for many platforms.

For example, on Ubuntu 18.10 and later:

```
sudo apt install flatpak
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

After completing installation and setup, browse and install Flatpak apps at https://flathub.org/home
