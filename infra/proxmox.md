# Proxmox Cheat-Sheet

## VM Management

| Command | Command Description |
| --- | --- |
| `qm list` | list VMs |
| `qm create <vm>` | Create or restore a virtual machine. |
| `qm start <vm>` | Start a VM |
| `qm suspend <vm>` | Suspend virtual machine. |
| `qm shutdown <vm>` | Shutdown a VM |
| `qm reboot <vm>` | Reboot a VM |
| `qm reset <vm>` | Reset a VM |
| `qm stop <vm>` | Stop a VM |
| `qm destroy <vm>` | Destroy the VM and all used/owned volumes. |
| `qm monitor <vm>` | Enter Qemu Monitor interface. |
| `qm pending <vm>` | Get the virtual machine configuration with both current and pending values. |
| `qm sendkey <vm> <key_event>` | Send key event to virtual machine. |
| `qm showcmd <vm>` | Show command line used to start the VM (debug info). |
| `qm unlock <vm>` | Unlock the VM |
| `qm clone <vm> <new_vm>` | Clone a VM |
| `qm migrate <vm> <node>` | Migrate a VM |
| `qm status <vm>` | Show VM status |
| `qm template <vm>` | Create a Template |
| `qm set <vm>` | Set virtual machine options (synchronous API) |

### Cloudinit

| Command | Command Description |
| --- | --- |
| `qm cloudinit dump <vm> <type>` | Get automatically generated cloudinit config. |
| `qm cloudinit pending <vm>` | Get the cloudinit configuration with both current and pending values. |
| `qm cloudinit update <vm>` | Regenerate and change cloudinit config drive. |

### Disk

| Command | Command Description |
| --- | --- |
| `qm disk import <vm> <source> <storage` | Import an external disk image as an unused disk in a VM. |
| `qm disk move <vm> <disk>` | Move volume to different storage or to a different VM. |
| `qm disk rescan` | Rescan all storages and update disk sizes and unused disk images. |
| `qm disk resize <vm> <disk> <size>` | Extend volume size. |
| `qm disk unlink <vm> --IDLIST <string>` | Unlink/delete disk images. |
| `qm rescan` | Rescan volumes. |
| `qemu-img convert <qcow2> <raw>` | Convert qcow2 to raw |
| `qemu-img convert -p -O qcow2 <raw> <qcow2>` | Convert back to qcow2 |

### Snapshot

| Command | Command Description |
| --- | --- |
| `qm listsnapshot <vm>` | List all snapshots. |
| `qm snapshot <vm> <snapshot>` | Snapshot a VM. |
| `qm delsnapshot <vm> <snapshot>` | Delete a snapshot. |
| `qm rollback <vm> <snapshot>` | Rollback a snapshot. |
| `qm terminal <vm>` | Open a terminal using a serial device. |
| `qm vncproxy <vm>` | Proxy VM VNC traffic to stdin/stdout. |

### Misc

| Command | Command Description |
| --- | --- |
| `qm guest cmd <vm> <command>` | Execute Qemu Guest Agent commands. |
| `qm guest exec <vm>` | Executes the given command via the guest agent. |
| `qm guest exec-status <vm> <pid>` | Gets the status of the given pid started by the guest-agent. |
| `qm guest passwd <vm> <user>` | Sets the password for the given user to the given password. |

### PV, VG, LV Management

| Command | Command Description |
| --- | --- |
| `pvcreate <disk>` | Create a PV |
| `pvremove <disk>` | Remove a PV |
| `pvs` | List all PVs |
| `vgcreate <vg> <disk>` | Create a VG |
| `vgremove <vg>` | Remove a VG |
| `vgs` | List all VGs |
| `lvcreate -L LV-SIZE -n <lv> <vg>` | Create a LV |
| `lvremove <vg>/<lv>` | Remove a LV |
| `lvs` | List all LVs |

### Storage Management

| Command | Command Description |
| --- | --- |
| `pvesm add TYPE <storage>` | Create a new storage |
| `pvesm alloc <storage> <vm> <file> <size>` | Allocate disk images |
| `pvesm free <volume>` | Delete volume |
| `pvesm remove <storage>` | Delete storage configuration |
| `pvesm list <storage>` | List storage content |
| `pvesm lvmscan` | An alias for pvesm scan lvm |
| `pvesm lvmthinscan` | An alias for pvesm scan lvmthin |
| `pvesm scan lvm` | List local LVM volume groups |
| `pvesm scan lvmthin VG` | List local LVM Thin Pools |
| `pvesm status` | Get status for all datastores |

### Template Management

| Command | Command Description |
| --- | --- |
| `pveam available` | List all templates |
| `pveam list <storage>` | List all templates |
| `pveam download <storage> <template>` | Download appliance templates |
| `pveam remove <template>` | Remove a template |
| `pveam update` | Update Container Template Database |

## Container Management

| Command | Command Description |
| --- | --- |
| `pct list` | List containers |
| `pct create <vm> OSTEMPLATE` | Create or restore a container |
| `pct start <vm>` | Start the container |
| `pct clone <vm> <new_vm>` | Create a container clone/copy |
| `pct suspend <vm>` | Suspend the container. This is experimental. |
| `pct resume <vm>` | Resume the container |
| `pct stop <vm>` | Stop the container. This will abruptly stop all processes running in the container. |
| `pct shutdown <vm>` | Shutdown the container. This will trigger a clean shutdown of the container. |
| `pct destroy <vm>` | Destroy the container (also delete all uses files) |
| `pct status <vm>` | Show CT status |
| `pct migrate <vm> <target>` | Migrate the container to another node. Creates a new migration task. |
| `pct config <vm>` | Get container configuration |
| `pct cpusets` | Print the list of assigned CPU sets |
| `pct pending <vm>` | Get container configuration, including pending changes |
| `pct reboot <vm>` | Reboot the container by shutting it down and starting it again. Applies pending changes. |
| `pct restore <vm> <template>` | Create or restore a container |
| `pct set <vm>` | Set container options |
| `pct template <vm>` | Create a Template |
| `pct unlock <vm>` | Unlock the VM |

### Container Disks

| Command | Command Description |
| --- | --- |
| `pct df <vm>` | Get the container’s current disk usage |
| `pct fsck <vm>` | Run a filesystem check (fsck) on a container volume |
| `pct fstrim <vm>` | Run fstrim on a chosen CT and its mountpoints |
| `pct mount <vm>` | Mount the container’s filesystem on the host |
| `pct move-volume <vm> <volume>` | Move a rootfs-/mp-volume to a different storage or to a different container |
| `pct unmount <vm>` | Unmount the container’s filesystem |
| `pct resize <vm> <disk> <size>` | Resize a container mount point |
| `pct rescan` | Rescan all storages and update disk sizes and unused disk images |
| `pct enter <vm>` | Connect to container |
| `pct console <vm>` | Launch a console for the specified container |
| `pct exec <vm>` | Launch a command inside the specified container |
| `pct pull <vm> <source> <destination>` | Copy a file from the container to the local system |
| `pct push <vm> <source> <destination>` | Copy a local file to the container |

## Web GUI

| Command | Command Description |
| --- | --- |
| `service pveproxy restart` | Restart the Proxmox web GUI |
