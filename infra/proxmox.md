# Proxmox Cheat-Sheet

Proxmox Virtual Environment (Proxmox VE or PVE) is a hyper-converged infrastructure open-source software. It is a hosted hypervisor that can run operating systems including Linux and Windows on x64 hardware. It is a Debian-based Linux distribution with a modified Ubuntu LTS kernel and allows deployment and management of virtual machines and containers. Proxmox VE includes a web console and command-line tools, and provides a REST API for third-party tools. Two types of virtualization are supported: container-based with LXC (starting from version 4.0 replacing OpenVZ used in version up to 3.4, included), and full virtualization with KVM. It includes a web-based management interface.

Proxmox VE is licensed under the GNU Affero General Public License, version 3.

Repository: [https://git.proxmox.com](https://git.proxmox.com)
Website: [https://pve.proxmox.com](https://pve.proxmox.com)

## VM Management

```shell
# list VMs
qm list

# Create or restore a virtual machine.
qm create your-vm-id

# start a VM
qm start your-vm-id

# Suspend virtual machine.
qm suspend your-vm-id

# shutdown a VM
qm shutdown your-vm-id

# reboot a VM
qm reboot your-vm-id

# reset a VM
qm reset your-vm-id

# stop a VM
qm stop your-vm-id

# Destroy the VM and all used/owned volumes.
# Removes any VM specific permissions and firewall rules
qm destroy your-vm-id

# Enter Qemu Monitor interface.
qm monitor your-vm-id

# Get the virtual machine configuration with both current and pending values.
qm pending your-vm-id

# Send key event to virtual machine.
qm sendkey your-vm-id your-key-event [OPTIONS]

# Show command line which is used to start the VM (debug info).
qm showcmd your-vm-id [OPTIONS]

# Unlock the VM.
qm unlock your-vm-id

# Clone a VM
qm clone your-vm-id new-vm-id

# Migrate a VM
qm migrate your-vm-id target-node

# Show VM status
qm status your-vm-id

# Clean up resources for a VM
qm cleanup your-vm-id your-clean-shutdown your-guest-requested

# Create a Template.
qm template your-vm-id [OPTIONS]

# Set virtual machine options (synchrounous API)
qm set your-vm-id [OPTIONS]
```

### Cloudinit

```shell
# Get automatically generated cloudinit config.
qm cloudinit dump your-vm-id your-vm-type

# Get the cloudinit configuration with both current and pending values.
qm cloudinit pending your-vm-id

# Regenerate and change cloudinit config drive.
qm cloudinit update your-vm-id
```

### Disk

```shell
# Import an external disk image as an unused disk in a VM.
# The image format has to be supported by qemu-img(1).
qm disk import your-vm-id your-target-source your-target-storage

# Move volume to different storage or to a different VM.
qm disk move your-vm-id your-vm-disk [<storage>] [OPTIONS]

# Rescan all storages and update disk sizes and unused disk images.
qm disk rescan [OPTIONS]

# Extend volume size.
qm disk resize your-vm-id your-vm-disk <size> [OPTIONS]

# Unlink/delete disk images.
qm disk unlink your-vm-id --idlist <string> [OPTIONS]

# rescan volumes
qm rescan
```

### Snapshot

```shell
# List all snapshots.
qm listsnapshot your-vm-id

# Snapshot a VM
qm snapshot your-vm-id <snapname>

# Delete a snapshot.
qm delsnapshot your-vm-id <snapname>

# Rollback a snapshot
qm rollback your-vm-id <snapname>

# Open a terminal using a serial device
# (The VM need to have a serial device configured, for example serial0: socket)
qm terminal your-vm-id [OPTIONS]

# Proxy VM VNC traffic to stdin/stdout
qm vncproxy your-vm-id
```

### Misc

```shell
# Execute Qemu Guest Agent commands.
qm guest cmd your-vm-id <command>

# Executes the given command via the guest agent
qm guest exec your-vm-id [<extra-args>] [OPTIONS]

# Gets the status of the given pid started by the guest-agent
qm guest exec-status your-vm-id <pid>

# Sets the password for the given user to the given password
qm guest passwd your-vm-id <username> [OPTIONS]
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
pvesm alloc <storage> your-vm-id <filename> <size> [OPTIONS]

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

```shell
# List containers
pct list

# Create or restore a container.
pct create your-vm-id <ostemplate> [OPTIONS]

# Start the container.
pct start your-vm-id [OPTIONS]

# Create a container clone/copy
pct clone your-vm-id new-vm-id [OPTIONS]

# Suspend the container. This is experimental.
pct suspend your-vm-id

# Resume the container.
pct resume your-vm-id

# Stop the container.
# This will abruptly stop all processes running in the container.
pct stop your-vm-id [OPTIONS]

# Shutdown the container.
# This will trigger a clean shutdown of the container, see lxc-stop(1) for details.
pct shutdown your-vm-id [OPTIONS]

# Destroy the container (also delete all uses files).
pct destroy your-vm-id [OPTIONS]

# Show CT status.
pct status your-vm-id [OPTIONS]

# Migrate the container to another node. Creates a new migration task.
pct migrate your-vm-id <target> [OPTIONS]

# Get container configuration.
pct config your-vm-id [OPTIONS]

# Print the list of assigned CPU sets.
pct cpusets

# Get container configuration, including pending changes.
pct pending your-vm-id

# Reboot the container by shutting it down, and starting it again. Applies pending changes.
pct reboot your-vm-id [OPTIONS]

# Create or restore a container.
pct restore your-vm-id <ostemplate> [OPTIONS]

# Set container options.
pct set your-vm-id [OPTIONS]

# Create a Template.
pct template your-vm-id

# Unlock the VM.
pct unlock your-vm-id
```

### Container Disks

```shell
# Get the container?s current disk usage.
pct df your-vm-id

# Run a filesystem check (fsck) on a container volume.
pct fsck your-vm-id [OPTIONS]

# Run fstrim on a chosen CT and its mountpoints.
pct fstrim your-vm-id [OPTIONS]

# Mount the container?s filesystem on the host.
# This will hold a lock on the container and is meant for emergency maintenance only
# as it will prevent further operations on the container other than start and stop.
pct mount your-vm-id

# Move a rootfs-/mp-volume to a different storage or to a different container.
pct move-volume your-vm-id <volume> [<storage>] [<target-vmid>] [<target-volume>] [OPTIONS]

# Unmount the container?s filesystem.
pct unmount your-vm-id

# Resize a container mount point.
pct resize your-vm-id your-vm-disk <size> [OPTIONS]

# Rescan all storages and update disk sizes and unused disk images.
pct rescan [OPTIONS]

# Connect to container
pct enter your-vm-id

# Launch a console for the specified container.
pct console your-vm-id [OPTIONS]

# Launch a shell for the specified container.
pct enter your-vm-id

# Launch a command inside the specified container.
pct exec your-vm-id [<extra-args>]

# Copy a file from the container to the local system.
pct pull your-vm-id <path> <destination> [OPTIONS]

# Copy a local file to the container.
pct push your-vm-id <file> <destination> [OPTIONS]
```

### Container Snapshot

```shell
# Snapshot a container.
pct snapshot your-vm-id <snapname> [OPTIONS]

# List all snapshots.
pct listsnapshot your-vm-id

# Rollback LXC state to specified snapshot.
pct rollback your-vm-id <snapname> [OPTIONS]

# Delete a LXC snapshot.
pct delsnapshot your-vm-id <snapname> [OPTIONS]
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

1. Convert qcow2 to raw: `qemu-img convert vm-100.qcow2 vm-100.raw`
2. Shrink the disk `qemu-img resize -f raw vm-100.raw 10G`
3. Convert back to qcow2 `qemu-img convert -p -O qcow2 vm-100.raw vm-100.qcow2`

## Further information

More examples and tutorials regarding Proxmox can be found in the link list below:

- Ansible playbook that automates Linux VM updates running on Proxmox (including snapshots): [TheDatabaseMe - update_proxmox_vm](https://github.com/thedatabaseme/update_proxmox_vm)
- Manage Proxmox VM templates with Packer: [Use Packer to build Proxmox images](https://thedatabaseme.de/2022/10/16/what-a-golden-boy-use-packer-to-build-proxmox-images/)
