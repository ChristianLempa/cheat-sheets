# Proxmox Terraform Integration

You can use [Terraform](tools/terraform.md) to automate certain tasks on [Proxmox](infra/proxmox.md). This allows you to manage virtual machines and lxc containers with infrastructure-as-code. We're using the third-party plugin [telmate/terraform-provider-proxmox](https://github.com/Telmate/terraform-provider-proxmox).

---
## Authenticate to Proxmox

### Create an API Token on Proxmox

WIP

### Add Provider config to Terraform

WIP

---
## Templates

WIP

---
## Useful commands

### Import existing virtual machines to Terraform

Existing virtual machines can be imported to the Terraform state file with the following command. Make sure, you have created a corresponding **Resource** in the **Terraform File**.

```
terraform import <resourcetype.resourcename> <id>
```

In the telmate/terraform-provider-proxmox, the id needs to be set according to `<node>/<type>/<vmid>`, like in the following example.

```
terraform import proxmox_vm_qemu.srv-prod-1 prx-prod-1/proxmox_vm_qemu/102
```


