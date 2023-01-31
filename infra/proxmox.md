# Proxmox Cheat-Sheet

Proxmox Virtual Environment (Proxmox VE or PVE) is a hyper-converged infrastructure open-source software. It is a hosted hypervisor that can run operating systems including Linux and Windows on x64 hardware. It is a Debian-based Linux distribution with a modified Ubuntu LTS kernel and allows deployment and management of virtual machines and containers. Proxmox VE includes a web console and command-line tools, and provides a REST API for third-party tools. Two types of virtualization are supported: container-based with LXC (starting from version 4.0 replacing OpenVZ used in version up to 3.4, included), and full virtualization with KVM. It includes a web-based management interface.

Proxmox VE is licensed under the GNU Affero General Public License, version 3.

Repository: https://git.proxmox.com

Website: https://pve.proxmox.com

## VM Management

### Basic

```shell
# list VMs
qm list

# Create or restore a virtual machine.
qm create <vmid>

# start a VM
qm start <vmid>

# Suspend virtual machine.
qm suspend <vmid>

# shutdown a VM
qm shutdown <vmid>

# reboot a VM
qm reboot <vmid>

# reset a VM
qm reset <vmid>

# stop a VM
qm stop <vmid>

# Destroy the VM and all used/owned volumes.
# Removes any VM specific permissions and firewall rules
qm destroy <vmid>

# Enter Qemu Monitor interface.
qm monitor <vmid>

# Get the virtual machine configuration with both current and pending values.
qm pending <vmid>

# Send key event to virtual machine.
qm sendkey <vmid> <key> [OPTIONS]

# Show command line which is used to start the VM (debug info).
qm showcmd <vmid> [OPTIONS]

# Unlock the VM.
qm unlock <vmid>

# Clone a VM
qm clone <vmid> <newid>

# Migrate a VM
qm migrate <vmid> <target-node>

# Show VM status
qm status <vmid>

# Clean up resources for a VM
qm cleanup <vmid> <clean-shutdown> <guest-requested>

# Create a Template.
qm template <vmid> [OPTIONS]

# Set virtual machine options (synchrounous API)
qm set <vmid> [OPTIONS]
```

### Cloudinit

```shell
# Get automatically generated cloudinit config.
qm cloudinit dump <vmid> <type>

# Get the cloudinit configuration with both current and pending values.
qm cloudinit pending <vmid>

# Regenerate and change cloudinit config drive.
qm cloudinit update <vmid>
```

### Disk

```shell
# Import an external disk image as an unused disk in a VM.
# The image format has to be supported by qemu-img(1).
qm disk import <vmid> <source> <storage>

# Move volume to different storage or to a different VM.
qm disk move <vmid> <disk> [<storage>] [OPTIONS]

# Rescan all storages and update disk sizes and unused disk images.
qm disk rescan [OPTIONS]

# Extend volume size.
qm disk resize <vmid> <disk> <size> [OPTIONS]

# Unlink/delete disk images.
qm disk unlink <vmid> --idlist <string> [OPTIONS]

# rescan volumes
qm rescan
```

### Snapshot

```shell
# List all snapshots.
qm listsnapshot <vmid>

# Snapshot a VM
qm snapshot <vmid> <snapname>

# Delete a snapshot.
qm delsnapshot <vmid> <snapname>

# Rollback a snapshot
qm rollback <vmid> <snapname>

# Open a terminal using a serial device
# (The VM need to have a serial device configured, for example serial0: socket)
qm terminal <vmid> [OPTIONS]

# Proxy VM VNC traffic to stdin/stdout
qm vncproxy <vmid>
```

### Misc

```shell
# Execute Qemu Guest Agent commands.
qm guest cmd <vmid> <command>

# Executes the given command via the guest agent
qm guest exec <vmid> [<extra-args>] [OPTIONS]

# Gets the status of the given pid started by the guest-agent
qm guest exec-status <vmid> <pid>

# Sets the password for the given user to the given password
qm guest passwd <vmid> <username> [OPTIONS]
```

### PV, VG, LV Management

```shell
# Create a PV
pvcreate <disk-device-name>

# Remove a PV
pvremove <disk-device-name>

# List all PVs
pvs

# Create a VG
vgcreate <vg-name> <disk-device-name>

# Remove a VG
vgremove <vg-name>

# List all VGs
vgs

# Create a LV
lvcreate -L <lv-size> -n <lv-name> <vg-name>

# Remove a LV
lvremove <vg-name>/<lv-name>

# List all LVs
lvs
```

### Storage Management

```shell
# Create a new storage.
pvesm add <type> <storage> [OPTIONS]

# Allocate disk images.
pvesm alloc <storage> <vmid> <filename> <size> [OPTIONS]

# Delete volume
pvesm free <volume> [OPTIONS]

# Delete storage configuration.
pvesm remove <storage>

# List storage content.
pvesm list <storage> [OPTIONS]

# An alias for pvesm scan lvm.
pvesm lvmscan

# An alias for pvesm scan lvmthin.
pvesm lvmthinscan

# List local LVM volume groups.
pvesm scan lvm

# List local LVM Thin Pools.
pvesm scan lvmthin <vg>

# Get status for all datastores.
pvesm status [OPTIONS]
```

### Template Management

```shell
# list all templates
pveam available

# list all templates
pveam list <storage>

# Download appliance templates
pveam download <storage> <template>

# Remove a template.
pveam remove <template-path>

# Update Container Template Database.
pveam update
```

## Certificate Management

See the [Proxmox Certificate Management](proxmox-certificate-management.md) cheat sheet.

## Container Management

### Basic

```shell
# List containers
pct list

# Create or restore a container.
pct create <vmid> <ostemplate> [OPTIONS]

# Start the container.
pct start <vmid> [OPTIONS]

# Create a container clone/copy
pct clone <vmid> <newid> [OPTIONS]

# Suspend the container. This is experimental.
pct suspend <vmid>

# Resume the container.
pct resume <vmid>

# Stop the container.
# This will abruptly stop all processes running in the container.
pct stop <vmid> [OPTIONS]

# Shutdown the container.
# This will trigger a clean shutdown of the container, see lxc-stop(1) for details.
pct shutdown <vmid> [OPTIONS]

# Destroy the container (also delete all uses files).
pct destroy <vmid> [OPTIONS]

# Show CT status.
pct status <vmid> [OPTIONS]

# Migrate the container to another node. Creates a new migration task.
pct migrate <vmid> <target> [OPTIONS]

# Get container configuration.
pct config <vmid> [OPTIONS]

# Print the list of assigned CPU sets.
pct cpusets

# Get container configuration, including pending changes.
pct pending <vmid>

# Reboot the container by shutting it down, and starting it again. Applies pending changes.
pct reboot <vmid> [OPTIONS]

# Create or restore a container.
pct restore <vmid> <ostemplate> [OPTIONS]

# Set container options.
pct set <vmid> [OPTIONS]

# Create a Template.
pct template <vmid>

# Unlock the VM.
pct unlock <vmid>
```

### Container Disks

```shell
# Get the container?s current disk usage.
pct df <vmid>

# Run a filesystem check (fsck) on a container volume.
pct fsck <vmid> [OPTIONS]

# Run fstrim on a chosen CT and its mountpoints.
pct fstrim <vmid> [OPTIONS]

# Mount the container?s filesystem on the host.
# This will hold a lock on the container and is meant for emergency maintenance only
# as it will prevent further operations on the container other than start and stop.
pct mount <vmid>

# Move a rootfs-/mp-volume to a different storage or to a different container.
pct move-volume <vmid> <volume> [<storage>] [<target-vmid>] [<target-volume>] [OPTIONS]

# Unmount the container?s filesystem.
pct unmount <vmid>

# Resize a container mount point.
pct resize <vmid> <disk> <size> [OPTIONS]

# Rescan all storages and update disk sizes and unused disk images.
pct rescan [OPTIONS]

# Connect to container
pct enter <vmid>

# Launch a console for the specified container.
pct console <vmid> [OPTIONS]

# Launch a shell for the specified container.
pct enter <vmid>

# Launch a command inside the specified container.
pct exec <vmid> [<extra-args>]

# Copy a file from the container to the local system.
pct pull <vmid> <path> <destination> [OPTIONS]

# Copy a local file to the container.
pct push <vmid> <file> <destination> [OPTIONS]
```

### Container Snapshot

```shell
# Snapshot a container.
pct snapshot <vmid> <snapname> [OPTIONS]

# List all snapshots.
pct listsnapshot <vmid>

# Rollback LXC state to specified snapshot.
pct rollback <vmid> <snapname> [OPTIONS]

# Delete a LXC snapshot.
pct delsnapshot <vmid> <snapname> [OPTIONS]
```

## Web GUI

```shell
# Restart web GUI
service pveproxy restart
```

## Resize Disk
### Increase disk size
Increase disk size in the GUI or with the following command
```shell
qm resize 100 virtio0 +5G
```

### Decrease disk size
> Before decreasing disk sizes in Proxmox, you should take a backup!
1. Convert qcow2 to raw
```shell
qemu-img convert vm-100.qcow2 vm-100.raw
```
2. Shrink the disk
```shell
qemu-img resize -f raw vm-100.raw 10G
```
3. Convert back to qcow2#
```shell
qemu-img convert -p -O qcow2 vm-100.raw vm-100.qcow2
```

## Further information

More examples and tutorials regarding Proxmox can be found in the link list below:

- Ansible playbook that automates Linux VM updates running on Proxmox (including snapshots): [TheDatabaseMe - update_proxmox_vm](https://github.com/thedatabaseme/update_proxmox_vm)
- Manage Proxmox VM templates with Packer: [Use Packer to build Proxmox images](https://thedatabaseme.de/2022/10/16/what-a-golden-boy-use-packer-to-build-proxmox-images/)
