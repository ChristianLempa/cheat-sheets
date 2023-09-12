# LVM2 (Logical Volume Manager 2)

**LVM2 (Logical Volume Manager 2)** is a utility for managing disk storage in [Linux](linux.md). It allows you to manage disk space efficiently by abstracting physical storage devices into logical volumes. It provides features like volume resizing, snapshotting, and striping, making it flexible and scalable for various storage needs.

1. Physical Volume: Represents the physical storage devices (e.g., hard drives, SSDs) that are part of the storage pool managed by LVM.

2. Volume Group: Combines multiple physical volumes into a unified storage pool, enabling easy management and allocation of logical volumes.

3. Logical Volume: Serves as a virtual disk that can be used for various purposes, such as creating partitions, mounting file systems, or even setting up RAID configurations.

4. File System: Represents the data organization and access methods used to store and retrieve data on a logical volume. Common file systems include EXT4, XFS, and Btrfs.

## Physical Volume (PV)

A Physical Volume (PV) in LVM is a physical storage device or partition used by LVM. It is a building block for creating Volume Groups and Logical Volumes, allowing you to manage storage efficiently. This command creates the PV on the devices, you can do multiple at a time.

```bash
sudo pvcreate /dev/Device /dev/Device2
```

The `pvdisplay` command provides a output for each physical volume. It displays physical properties like size, extents, volume group, and so on in a fixed format.

```bash
sudo pvdisplay
```

The pvscan command scans all physical volumes (PVs) on the system and displays information about them.

```bash
sudo pvscan
```

Moves the allocated physical extents from one physical volume to another. Useful when you need to redistribute space between physical volumes in a volume group. After a crash or power failure this can be finished without a problem.

```bash
sudo pvmove /dev/source_device /dev/target_device
```

## Volume Group (VG)

A Volume Group (VG) in LVM is a collection of one or more Physical Volumes (PVs) combined into a single storage pool. It allows flexible and efficient management of disk space, enabling easy allocation to Logical Volumes (LVs) as needed.

Creates a volume group with a specified name.

```bash
sudo vgcreate Volume_Name /dev/Device1 /dev/Device2 ...
```

The `vgdisplay` command displays volume group properties (such as size, extents, number of physical volumes, and so on) in a fixed form.

```bash
sudo vgdisplay
```

The `vgs` command provides volume group information in a configurable form, displaying one line per volume group. The `vgs` command provides a great deal of format control, and is useful for scripting.

```bash
sudo vgs
```

## Logical Volume (LV)

A logical volume in LVM is a flexible virtual partition that separates storage management from physical disks. This creates a logical volume out of the Volume Group with the specified name and size (5GB).

```bash
sudo lvcreate -n Volume -L 5g Group
```

Extends the logical volume by all the available space from the volume group. U can also extend it to a fixed size if u don't use the `+`.

```bash
sudo lvextend -L +100%FREE Group/Volume
```

Same as above but in the other direction.

```bash
sudo lvreduce -L -5g Group/Volume
```

This is how u rename a logical volume.

```bash
sudo lvrename /dev/Group/old_LV_name new_LV_name
```

This removes a logical volume. Use this command with extreme caution, as it will permanently delete the data on the logical volume.

```bash
sudo lvremove /dev/Group/Volume
```

The `lvs` command provides logical volume information in a configurable form, displaying one line per logical volume. The `lvs` command provides a great deal of format control, and is useful for scripting.

```bash
sudo lvs
```

The `lvdisplay` command displays logical volume properties (such as size, layout, and mapping) in a fixed format.

```bash
sudo lvdisplay
```

### File System

After extending a logical volume, use this command to expand the file system to use the new space.

```bash
sudo resize2fs /dev/Group/Volume
```

## Snapshots

Snapshots in LVM are copies of a logical volume at a specific time, useful for backups and data recovery. This creates a snapshot named "snap" with 5GB. Snapshots store only the changes made since their creation and are independent of the original volume. 

```bash
sudo lvcreate -s -n snap -L 5g Group/Volume
```

Merges the snapshot with the original volume. Useful after a faulty update; requires a reboot.

```bash
sudo lvconvert --merge Group/snap
```

## Cache

This creates a cache logical volume with the "writethrough" cache mode using 100% of the free space. Caching improves disk read/write performance. Writethrough ensures that any data written will be stored both in the cache and on the origin LV. The loss of a device associated with the cache in this case would not mean the loss of any data. A second cache mode is "writeback". Writeback delays writing data blocks from the cache back to the origin LV.

```bash
sudo lvcreate --type cache --cachemode writethrough -l 100%FREE -n root_cachepool MyVolGroup/rootvol /dev/fastdisk
```

This removes the cache from the specified logical volume.

```bash
sudo lvconvert --uncache MyVolGroup/rootvol
```

## RAID

> LVM Is Using md Under the Hood

This configuring below will still use "md" behind the scenes. It just saves you the trouble of using "mdadm".

#### RAID 0

RAID 0 is a data storage configuration that stripes data across multiple drives to improve performance, but offers no data redundancy, meaning a single drive failure can result in data loss. This creates a RAID 0 logical volume with a specified name using 100% of the free space in the volume group, with the specified stripe size (2GB).

```bash
sudo lvcreate -i Stripes -I 2G -l 100%FREE -n Volume Group
```

#### RAID 1

RAID 1 is a data storage configuration that mirrors data across multiple drives for data redundancy, providing fault tolerance in case of drive failure but without the performance improvement of RAID 0. This creates a RAID 1 logical volume with a specified name using 100% of the free space in the volume group. The `--nosync` option skips initial sync.

```bash
sudo lvcreate --mirrors 1 --type raid1 -l 100%FREE --nosync -n Volume VGName
```

#### RAID 5

RAID 5 is a data storage configuration that combines striping and parity to provide both performance improvement and data redundancy, allowing for continued data access even if a single drive fails. This creates a RAID 5 logical volume with a specified name using 100% of the free space in the volume group. RAID 5 offers both data striping and parity for fault tolerance.

```bash
sudo lvcreate --type raid5 -l 100%FREE -n LVName VGName
```
