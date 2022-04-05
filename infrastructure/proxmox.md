# Proxmox Cheat-Sheets
## Resize Disk
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
