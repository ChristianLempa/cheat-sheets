# Proxmox Cheat-Sheet

## VM Management

| Command | Command Description |
| --- | --- |
| `qm list` | list VMs |
| `qm create VM_ID` | Create or restore a virtual machine. |
| `qm start VM_ID` | Start a VM |
| `qm suspend VM_ID` | Suspend virtual machine. |
| `qm shutdown VM_ID` | Shutdown a VM |
| `qm reboot VM_ID` | Reboot a VM |
| `qm reset VM_ID` | Reset a VM |
| `qm stop VM_ID` | Stop a VM |
| `qm destroy VM_ID` | Destroy the VM and all used/owned volumes. |
| `qm monitor VM_ID` | Enter Qemu Monitor interface. |
| `qm pending VM_ID` | Get the virtual machine configuration with both current and pending values. |
| `qm sendkey VM_ID YOUR_KEY_EVENT [OPTIONS]` | Send key event to virtual machine. |
| `qm showcmd VM_ID [OPTIONS]` | Show command line used to start the VM (debug info). |
| `qm unlock VM_ID` | Unlock the VM |
| `qm clone VM_ID NEW_VM_ID` | Clone a VM |
| `qm migrate VM_ID TARGET_NODE` | Migrate a VM |
| `qm status VM_ID` | Show VM status |
| `qm cleanup VM_ID CLEAN_SHUTDOWN GUEST_REQUESTED` | Clean up resources for a VM |
| `qm template VM_ID [OPTIONS]` | Create a Template |
| `qm set VM_ID [OPTIONS]` | Set virtual machine options (synchronous API) |

### Cloudinit

| Command | Command Description |
| --- | --- |
| `qm cloudinit dump VM_ID VM_TYPE` | Get automatically generated cloudinit config. |
| `qm cloudinit pending VM_ID` | Get the cloudinit configuration with both current and pending values. |
| `qm cloudinit update VM_ID` | Regenerate and change cloudinit config drive. |

### Disk

| Command | Command Description |
| --- | --- |
| `qm disk import VM_ID TARGET_SOURCE TARGET_STORAGE` | Import an external disk image as an unused disk in a VM. |
| `qm disk move VM_ID VM_DISK [STORAGE] [OPTIONS]` | Move volume to different storage or to a different VM. |
| `qm disk rescan [OPTIONS]` | Rescan all storages and update disk sizes and unused disk images. |
| `qm disk resize VM_ID VM_DISK SIZE [OPTIONS]` | Extend volume size. |
| `qm disk unlink VM_ID --IDLIST STRING [OPTIONS]` | Unlink/delete disk images. |
| `qm rescan` | Rescan volumes. |
| `qemu-img convert VM_ID.qcow2 VM_ID.raw` | Convert qcow2 to raw |
| `qemu-img convert -p -O qcow2 VM_ID.raw VM_ID.qcow2` | Convert back to qcow2 |

### Snapshot

| Command | Command Description |
| --- | --- |
| `qm listsnapshot VM_ID` | List all snapshots. |
| `qm snapshot VM_ID SNAPNAME` | Snapshot a VM. |
| `qm delsnapshot VM_ID SNAPNAME` | Delete a snapshot. |
| `qm rollback VM_ID SNAPNAME` | Rollback a snapshot. |
| `qm terminal VM_ID [OPTIONS]` | Open a terminal using a serial device. |
| `qm vncproxy VM_ID` | Proxy VM VNC traffic to stdin/stdout. |

### Misc

| Command | Command Description |
| --- | --- |
| `qm guest cmd VM_ID COMMAND` | Execute Qemu Guest Agent commands. |
| `qm guest exec VM_ID [EXTRA-ARGS] [OPTIONS]` | Executes the given command via the guest agent. |
| `qm guest exec-status VM_ID PID` | Gets the status of the given pid started by the guest-agent. |
| `qm guest passwd VM_ID USERNAME [OPTIONS]` | Sets the password for the given user to the given password. |

### PV, VG, LV Management

| Command | Command Description |
| --- | --- |
| `pvcreate DISK-DEVICE-NAME` | Create a PV |
| `pvremove DISK-DEVICE-NAME` | Remove a PV |
| `pvs` | List all PVs |
| `vgcreate VG-NAME DISK-DEVICE-NAME` | Create a VG |
| `vgremove VG-NAME` | Remove a VG |
| `vgs` | List all VGs |
| `lvcreate -L LV-SIZE -n LV-NAME VG-NAME` | Create a LV |
| `lvremove VG-NAME/LV-NAME` | Remove a LV |
| `lvs` | List all LVs |

### Storage Management

| Command | Command Description |
| --- | --- |
| `pvesm add TYPE STORAGE [OPTIONS]` | Create a new storage |
| `pvesm alloc STORAGE your-vm-id FILENAME SIZE [OPTIONS]` | Allocate disk images |
| `pvesm free VOLUME [OPTIONS]` | Delete volume |
| `pvesm remove STORAGE` | Delete storage configuration |
| `pvesm list STORAGE [OPTIONS]` | List storage content |
| `pvesm lvmscan` | An alias for pvesm scan lvm |
| `pvesm lvmthinscan` | An alias for pvesm scan lvmthin |
| `pvesm scan lvm` | List local LVM volume groups |
| `pvesm scan lvmthin VG` | List local LVM Thin Pools |
| `pvesm status [OPTIONS]` | Get status for all datastores |

### Template Management

| Command | Command Description |
| --- | --- |
| `pveam available` | List all templates |
| `pveam list STORAGE` | List all templates |
| `pveam download STORAGE TEMPLATE` | Download appliance templates |
| `pveam remove TEMPLATE-PATH` | Remove a template |
| `pveam update` | Update Container Template Database |

## Container Management

| Command | Command Description |
| --- | --- |
| `pct list` | List containers |
| `pct create YOUR-VM-ID OSTEMPLATE [OPTIONS]` | Create or restore a container |
| `pct start YOUR-VM-ID [OPTIONS]` | Start the container |
| `pct clone YOUR-VM-ID NEW-VM-ID [OPTIONS]` | Create a container clone/copy |
| `pct suspend YOUR-VM-ID` | Suspend the container. This is experimental. |
| `pct resume YOUR-VM-ID` | Resume the container |
| `pct stop YOUR-VM-ID [OPTIONS]` | Stop the container. This will abruptly stop all processes running in the container. |
| `pct shutdown YOUR-VM-ID [OPTIONS]` | Shutdown the container. This will trigger a clean shutdown of the container. |
| `pct destroy YOUR-VM-ID [OPTIONS]` | Destroy the container (also delete all uses files) |
| `pct status YOUR-VM-ID [OPTIONS]` | Show CT status |
| `pct migrate YOUR-VM-ID TARGET [OPTIONS]` | Migrate the container to another node. Creates a new migration task. |
| `pct config YOUR-VM-ID [OPTIONS]` | Get container configuration |
| `pct cpusets` | Print the list of assigned CPU sets |
| `pct pending YOUR-VM-ID` | Get container configuration, including pending changes |
| `pct reboot YOUR-VM-ID [OPTIONS]` | Reboot the container by shutting it down and starting it again. Applies pending changes. |
| `pct restore YOUR-VM-ID OSTEMPLATE [OPTIONS]` | Create or restore a container |
| `pct set YOUR-VM-ID [OPTIONS]` | Set container options |
| `pct template YOUR-VM-ID` | Create a Template |
| `pct unlock YOUR-VM-ID` | Unlock the VM |

### Container Disks

| Command | Command Description |
| --- | --- |
| `pct df YOUR-VM-ID` | Get the container’s current disk usage |
| `pct fsck YOUR-VM-ID [OPTIONS]` | Run a filesystem check (fsck) on a container volume |
| `pct fstrim YOUR-VM-ID [OPTIONS]` | Run fstrim on a chosen CT and its mountpoints |
| `pct mount YOUR-VM-ID` | Mount the container’s filesystem on the host |
| `pct move-volume YOUR-VM-ID VOLUME [STORAGE] [TARGET-VMID] [TARGET-VOLUME] [OPTIONS]` | Move a rootfs-/mp-volume to a different storage or to a different container |
| `pct unmount YOUR-VM-ID` | Unmount the container’s filesystem |
| `pct resize YOUR-VM-ID YOUR-VM-DISK SIZE [OPTIONS]` | Resize a container mount point |
| `pct rescan [OPTIONS]` | Rescan all storages and update disk sizes and unused disk images |
| `pct enter YOUR-VM-ID` | Connect to container |
| `pct console YOUR-VM-ID [OPTIONS]` | Launch a console for the specified container |
| `pct exec YOUR-VM-ID [EXTRA-ARGS]` | Launch a command inside the specified container |
| `pct pull YOUR-VM-ID PATH DESTINATION [OPTIONS]` | Copy a file from the container to the local system |
| `pct push YOUR-VM-ID FILE DESTINATION [OPTIONS]` | Copy a local file to the container |

## Web GUI

| Command | Command Description |
| --- | --- |
| `service pveproxy restart` | Restart the Proxmox web GUI |
