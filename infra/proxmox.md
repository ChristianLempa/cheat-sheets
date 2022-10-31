# Proxmox
WIP

---
## ACME Certificates
WIP

1. datacenter -> acme -> add account
2. datacenter -> acme -> add challenge plugin
3. node -> certificates -> acme -> use account
4. node -> certificates -> acme -> add certs
5. node -> certificates -> acme -> order certificates now

--- 
## Resize Disk
WIP

### Increase disk size
Increase disk size in the GUI or with the following command
```
qm resize 100 virtio0 +5G
```

### Decrease disk size
> Before decreasing disk sizes in Proxmox, you should take a backup!
1. Convert qcow2 to raw
```
qemu-img convert vm-100.qcow2 vm-100.raw
```
2. Shrink the disk
```
qemu-img resize -f raw vm-100.raw 10G
```
3. Convert back to qcow2#
```
qemu-img convert -p -O qcow2 vm-100.raw vm-100.qcow2
```

---
## Further information

More examples and tutorials regarding Proxmox can be found in the link list below:

- Ansible playbook that automates Linux VM updates running on Proxmox (including snapshots): [TheDatabaseMe - update_proxmox_vm](https://github.com/thedatabaseme/update_proxmox_vm)
- Manage Proxmox VM templates with Packer: [Use Packer to build Proxmox images](https://thedatabaseme.de/2022/10/16/what-a-golden-boy-use-packer-to-build-proxmox-images/)