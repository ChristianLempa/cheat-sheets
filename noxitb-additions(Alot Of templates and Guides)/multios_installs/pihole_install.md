# Installing Pi-hole on Various Linux Distributions

Pi-hole is a popular network-wide ad blocker that acts as a DNS sinkhole. It blocks ads and trackers at the network level, providing an ad-free browsing experience for all devices on your network. Here are the instructions for installing Pi-hole on different Linux distributions:

## Ubuntu 20.04 and 22.04

1. Update the package list: `sudo apt update`.
2. Install the required dependencies: `sudo apt install -y curl`.
3. Download the Pi-hole installer script: `curl -sSL https://install.pi-hole.net | sudo bash`.
4. Follow the on-screen prompts to configure Pi-hole.
5. Access the Pi-hole admin interface by visiting `http://<your_server_ip>/admin`.

## CentOS 8

1. Install the required dependencies: `sudo dnf install -y curl`.
2. Download the Pi-hole installer script: `curl -sSL https://install.pi-hole.net | sudo bash`.
3. Follow the on-screen prompts to configure Pi-hole.
4. Access the Pi-hole admin interface by visiting `http://<your_server_ip>/admin`.

## Debian 10

1. Update the package list: `sudo apt update`.
2. Install the required dependencies: `sudo apt install -y curl`.
3. Download the Pi-hole installer script: `curl -sSL https://install.pi-hole.net | sudo bash`.
4. Follow the on-screen prompts to configure Pi-hole.
5. Access the Pi-hole admin interface by visiting `http://<your_server_ip>/admin`.

## AlmaLinux 8

1. Install the required dependencies: `sudo dnf install -y curl`.
2. Download the Pi-hole installer script: `curl -sSL https://install.pi-hole.net | sudo bash`.
3. Follow the on-screen prompts to configure Pi-hole.
4. Access the Pi-hole admin interface by visiting `http://<your_server_ip>/admin`.

## Fedora 34

1. Install the required dependencies: `sudo dnf install -y curl`.
2. Download the Pi-hole installer script: `curl -sSL https://install.pi-hole.net | sudo bash`.
3. Follow the on-screen prompts to configure Pi-hole.
4. Access the Pi-hole admin interface by visiting `http://<your_server_ip>/admin`.

## openSUSE Leap 15.2

1. Install the required dependencies: `sudo zypper install -y curl`.
2. Download the Pi-hole installer script: `curl -sSL https://install.pi-hole.net | sudo bash`.
3. Follow the on-screen prompts to configure Pi-hole.
4. Access the Pi-hole admin interface by visiting `http://<your_server_ip>/admin`.

That's it! You have successfully installed Pi-hole on various Linux distributions. Now you can enjoy ad-free browsing for all devices on your network.

Please note that this guide provides a general overview of the installation process and assumes you have a basic understanding of Linux package management. Make sure to review the specific documentation for each distribution for any distribution-specific instructions or troubleshooting steps.
