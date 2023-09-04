# Proxmox Terraform Integration

You can use [Terraform](tools/terraform.md) to automate certain tasks on [Proxmox](infra/proxmox.md). This allows you to manage virtual machines and lxc containers with infrastructure-as-code. We're using the third-party plugin [telmate/terraform-provider-proxmox](https://github.com/Telmate/terraform-provider-proxmox).

## Authenticate to Proxmox

### Create an API Token on Proxmox

To create a new API Token for your `user` in Proxmox, follow the steps described in [Proxmox API Authentication](proxmox-api.md).

### Add Provider config to Terraform

```json
terraform {
  required_version = ">= 0.13.0"

  required_providers {
    proxmox = {
      source = "telmate/proxmox"
      version = ">=2.9.14"
    }
  }
}
```

```json
variable "PROXMOX_URL" {
    type = string
}

variable "PROXMOX_USER" {
    type = string
}

variable "PROXMOX_TOKEN" {
    type = string
    sensitive = true
}

provider "proxmox" {
    pm_api_url = var.PROXMOX_URL
    pm_api_token_id = var.PROXMOX_USER
    pm_api_token_secret = var.PROXMOX_TOKEN
    pm_tls_insecure = false
}
```

## Templates

WIP

## Useful commands

### Import existing virtual machines to Terraform

Existing virtual machines can be imported to the Terraform state file with the following command. Make sure, you have created a corresponding **Resource** in the **Terraform File**.

```sh
terraform import <resourcetype.resourcename> <id>
```

In the telmate/terraform-provider-proxmox, the id needs to be set according to `<node>/<type>/<vmid>`, like in the following example.

```sh
terraform import proxmox_vm_qemu.srv-prod-1 prx-prod-1/proxmox_vm_qemu/102
```
