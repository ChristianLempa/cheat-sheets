# Packer

Create identical machine images for multiple platforms from a single source configuration.

Project Homepage: https://www.packer.io
Documentation: https://developer.hashicorp.com/packer/docs
Plugins: https://developer.hashicorp.com/packer/plugins 

---
## Installation


### macOS

```sh
brew tap hashicorp/tap
brew install hashicorp/tap/packer
```


### Windows

https://developer.hashicorp.com/packer/downloads


### Linux

#### Ubuntu/Debian

```sh
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update && sudo apt install packer
```


---
## Plugins

TODO: WIP


### Proxmox Builder

The [Proxmox](infra/proxmox.md) Packer builder is able to create virtual machines and store them as new images using [proxmox-clone](https://developer.hashicorp.com/packer/plugins/builders/proxmox/clone), and [proxmox-iso](https://developer.hashicorp.com/packer/plugins/builders/proxmox/iso).

#### Authentication

TODO: WIP

You can also use the [environment variables](linux/environment-variables-in-linux.md) `PROXMOX_URL`, `PROXMOX_USERNAME`, `PROXMOX_PASSWORD`, and `PROXMOX_TOKEN` to authenticate to [Proxmox](infra/proxmox.md).

#### Template

```hcl

WIP: TODO

```

