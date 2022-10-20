---
tags:
    - linux
    - pi
categories:
    - linux
---

# Raspberry Pi 4 Cheat Sheet

List of commands, configurations and tips for Raspberry Pi and Linux beginners. Also known as a quick start guide.

## Table of contents

* [Raspberry Pi OS / Linux](#raspberry-pi-os--linux)
* [Pi-hole](#pi-hole)
* [Git](#git)
* [Node.js](#nodejs)
* [Docker](#docker)
* [Speedtest.net](#speedtestnet)

## Raspberry Pi OS / Linux
### Pi user default password
Default password for pi user is "raspberry"

### Enable SSH
To enable SSH, which is disabled by default in Raspbian, just put an empty `ssh` file with no extension on `/boot` partition.

### Useful configs
Go to `/boot/config.txt` and add these entries in the end of the file.
##### Or directly from terminal
```
sudo nano /boot/config.txt
```
#### Overclocking
##### CPU
```
over_voltage=6
arm_freq=2000
core_freq=600
```

##### GPU
```
gpu_freq=750
gpu_mem=128
```

##### Override temperature limit
```
temp_limit=75
```

### Enable 64-bit kernel
```
arm_64bit=1
```

### Miscellaneous
#### Prevent HDMI TV from turning on when Raspberry Pi is booting
```
hdmi_ignore_cec_init=1
```

#### Disable splash screen
```
disable_splash=1
```

#### Disable Wi-Fi
```
dtoverlay=disable-wifi
```

#### Disable Bluetooth
```
dtoverlay=disable-bt
```

#### Disable camera
```
start_x=0
```

## Beta / stable releases

### Edit `rpi-eeprom-update` file
```
sudo nano /etc/default/rpi-eeprom-update
```
### and change content to
```
FIRMWARE_RELEASE_STATUS="beta"
```
### or
```
FIRMWARE_RELEASE_STATUS="stable"
```

## Shutdown / Reboot
### Shutdown
```
sudo shutdown -h now
```
### Reboot
```
sudo shutdown -r now
```
### Uptime
```
uptime -p
```
### Last boot time
```
uptime -s
```

## Kernel version
### Check kernel version and info
```
uname -a
```

## Working with PATH variable
### Print PATH variable line by line
```
echo $PATH | tr : '\n'.
```

### Add to PATH
```
export PATH=<path to be added>:$PATH
```

## Update / Upgrade everything
### One-liner
```
sudo apt-get update -y && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get autoremove -y && sudo rpi-eeprom-update -a
```
## Read system logs in real-time
### List last 30 lines from system logs and updates in real-time
```
tail -f -n 30 /var/log/syslog
```

## Audio
### Testing audio on default output
```
speaker-test -c2 -twav -l7
```

## MicroSD
### Benchmark
```
sudo apt install agnostics
```
```
sh /usr/share/agnostics/sdtest.sh
```

## Chromium / Chrome
### Chromium screen tearing fix
```
sudo rm /etc/xdg/autostart/xcompmgr.desktop
```

## Read temperature
### One time read CPU temp
```
echo "$(($(</sys/class/thermal/thermal_zone0/temp)/1000))'C"
```
### One time read GPU temp
```
vcgencmd measure_temp
```
### One time read GPU temp
```
watch -n 0.1 vcgencmd measure_temp
```

## RAM
### Currently free memory and swap usage
```
free -m
```

## Date
### Display date and time
```
date
```

## Cron
### View cron tab
```
crontab -e
```

### View Cron logs
```
grep CRON /var/log/syslog
```

## Repositories
### Add source
```
curl -sS https://download.spotify.com/debian/pubkey.gpg | sudo apt-key add - 
```

### List sources
```
sudo apt-key list
```

### Remove source
```
sudo apt-key del "2EBF 997C 15BD A244 B6EB  F5D8 4773 BD5E 130D 1D45"
```

## Connectivity
### Wi-Fi
#### Scan for nearby Wi-Fi networks
```
sudo iwlist wlan0 scan
```

#### Setup Wi-Fi password through terminal
```
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```
#### Add this entry to the file with changed SSID and Password
```
network={
    ssid="Wi-Fi SSID"
    psk="WiFI Password"
    key_mgmt=WPA-PSK
}
```

### Bluetooth
#### Scan for nearby bluetooth devices
```
sudo hcitool scan
```

## Network
### Check public IP
```
curl ifconfig.me
```

## Pi-hole
### Installation
#### Original instruction is missing `sudo` for bash
```
sudo curl -sSL https://install.pi-hole.net | sudo bash
```

#### Repair install
```
pihole reconfigure
```

#### Set password
##### Set password for the dashboard or completely remove it
```
pihole -a -p
```

#### Upgrade Pi-hole
##### Download and install the latest version
```
pihole -up
```

#### Pi-hole Crontab
##### Edit pi-hole crontab for auto-updates
```
sudo nano /etc/cron.d/pihole
```
##### And change appropriate line to in example:
```
0 2 * * *   root    PATH="$PATH:/usr/sbin:/usr/local/bin/" pihole updateGravity >/var/log/pihole_updateGravity.log || cat /var/log/pihole_updateGravity.log
```
##### Which means every day at 2AM

#### Update Gravity
##### Download latest blocklists
```
pihole updateGravity
```

#### Gravity update logs
##### Read last gravity update logs or watch it in real-time.
```
tail -f -n 30 /var/log/pihole_updateGravity.log
```

#### Set additional DNS servers
##### Pi-hole dashboard allows to set only 1 custom DNS server
```
sudo nano /etc/pihole/setupVars.conf
```
##### Then add new servers like this
```
PIHOLE_DNS_1=8.8.8.8
PIHOLE_DNS_2=2001:4860:4860:0:0:0:0:8888
PIHOLE_DNS_3=1.1.1.1
PIHOLE_DNS_4=2606:4700:4700::1111
PIHOLE_DNS_5=62.179.1.60
PIHOLE_DNS_6=62.179.1.61
PIHOLE_DNS_7=62.179.1.62
PIHOLE_DNS_8=62.179.1.63
```
##### Restart service
```
sudo service pihole-FTL restart
```

## Git
### Configuration
#### Create store for user credentials
```
git config --global credential.helper store
```

#### Set account's default identity
```
git config --global user.email "lukaszlapaj@interia.pl"
git config --global user.name "Lukasz Lapaj"
```

## Node.js
### Installation
#### Preinstalled Raspberry Pi OS repository version is outdated, use version below:
```
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs
```

## Docker
### Installation
#### Remove old versions
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```
#### Install pre-requirements
```
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```
#### Add Docker’s official GPG key
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
#### Install docker
```
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## Speedtest.net
### Installation
#### Pre-requirements
```
sudo apt-get install gnupg1 apt-transport-https dirmngr
export INSTALL_KEY=379CE192D401AB61
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $INSTALL_KEY
echo "deb https://ookla.bintray.com/debian generic main" | sudo tee  /etc/apt/sources.list.d/speedtest.list
```
#### Install
```
sudo apt-get install speedtest
```

## See also

- [Linux](linux.md)
- [Shell commands](shell-commands.md)
