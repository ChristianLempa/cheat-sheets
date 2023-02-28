# Fedora

Fedora Linux is a Linux distribution developed by the Fedora Project. Fedora contains software distributed under various free and open-source licenses and aims to be on the leading edge of open-source technologies. Fedora is the upstream source for Red Hat Enterprise Linux.

Since the release of Fedora 35, six different editions are made available tailored to personal computer, server, cloud computing, container and Internet of Things installations. A new version of Fedora Linux is released every six months.

Project Homepage: [Home - Fedora](https://getfedora.org/en/)
Documentation: [Fedora Documentation](https://docs.fedoraproject.org/en-US/docs/)

---
## Post Install Steps

### 1- Enable Caching in dnf Package Manager
Caching is Enabled to increase dnf speed

Edit dnf configuration:
```shell
sudo nano /etc/dnf/dnf.conf
```
Add this lines add the end:
```shell
# Added for speed:
fastestmirror=True
#change to 10 if you have fast internet speed
max_parallel_downloads=5
#when click enter the default is yes
defaultyes=True
#Keeps downloaded packages in the cache
keepcache=True
```
To clean dnf cache periodically:
```shell
sudo dnf clean dbcache
#or
sudo dnf clean all
```
for more configuration options: [DNF Configuration Reference](https://dnf.readthedocs.io/en/latest/conf_ref.html)

### 2- System Update

Run the following command:
```shell
sudo dnf update
```

## 3- Enable RPM Fusion

RPM Fusion **provides software that the Fedora Project or Red Hat doesn't want to ship**. That software is provided as precompiled RPMs for all current Fedora versions and current Red Hat Enterprise Linux or clones versions; you can use the RPM Fusion repositories with tools like yum and PackageKit.

Installing both free and non-free RPM Fusion:
```shell
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

### AppStream metadata
to enable users to install packages using Gnome Software/KDE Discover. Please note that these are a subset of all packages since the metadata are only generated for GUI packages.

The following command will install the required packages:
```shell
sudo dnf groupupdate core
```

## 4- Adding Flatpak

Flatpak, formerly known as xdg-app, is a utility for software deployment and package management for Linux. It is advertised as offering a sandbox environment in which users can run application software in isolation from the rest of the system.

Flatpak is installed by default on Fedora Workstation, Fedora Silverblue, and Fedora Kinoite. To get started, all you need to do is enable **Flathub**, which is the best way to get Flatpak apps. Just download and install the [Flathub repository file](https://flathub.org/repo/flathub.flatpakrepo)

The above links should work on the default GNOME and KDE Fedora installations, but if they fail for some reason you can manually add the Flathub remote by running:
```shell
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

## 5- Change Hostname

Run the following command:
```shell
sudo hostnamectl set-hostname #your-name
```

## 6- Add Multimedia Codecs

Run the following commands:
```shell
sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin

sudo dnf groupupdate sound-and-video
```

## 7- Make it More  Customizable

Open GNOME software installer and install the following:
- GNOME Tweaks
- Extensions

Consider the following GNOME Extensions:
- Vitals
- ArcMenu
- Custom Hot Corners - Extended
- Dash to Panel
- Sound input & ouput Device Chooser
- OpenWeather
- Impatience
- Screenshot Tool
- Tiling Assistant
- Extension List
- Clipboard Indicator
