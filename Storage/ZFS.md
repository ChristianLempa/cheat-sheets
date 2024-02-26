# ZFS
WIP

Reference: [Oracle Solaris ZFS Administration Guide](https://docs.oracle.com/cd/E19253-01/819-5461/index.html)

---
## Storage Pools
WIP

### Stripe

ZFS dynamically stripes data across all top-level virtual devices. The decision about where to place data is done at write time, so no fixed-width stripes are created at allocation time.

When new virtual devices are added to a pool, ZFS gradually allocates data to the new device in order to maintain performance and disk space allocation policies. Each virtual device can also be a mirror or a RAID-Z device that contains other disk devices or files. This configuration gives you flexibility in controlling the fault characteristics of your pool. 

Although ZFS supports combining different types of virtual devices within the same pool, avoid this practice. For example, you can create a pool with a two-way mirror and a three-way RAID-Z configuration. However, your fault tolerance is as good as your worst virtual device, RAID-Z in this case. A best practice is to use top-level virtual devices of the same type with the same redundancy level in each device.

### Mirror

A mirrored storage pool configuration requires at least two disks, preferably on separate controllers. Many disks can be used in a mirrored configuration. In addition, you can create more than one mirror in each pool. 

### Striped Mirror

Data is dynamically striped across both mirrors, with data being redundant between each disk appropriately.

Currently, the following operations are supported in a ZFS mirrored configuration:
- Adding another set of disks for an additional top-level virtual device (vdev) to an existing mirrored configuration.
- Attaching additional disks to an existing mirrored configuration. Or, attaching additional disks to a non-replicated configuration to create a mirrored configuration.
- Replacing a disk or disks in an existing mirrored configuration as long as the replacement disks are greater than or equal to the size of the device to be replaced.
- Detaching a disk in a mirrored configuration as long as the remaining devices provide adequate redundancy for the configuration.
- Splitting a mirrored configuration by detaching one of the disks to create a new, identical pool.

### RAID-Z

In addition to a mirrored storage pool configuration, **ZFS provides a RAID-Z configuration with either single-, double-, or triple-parity fault tolerance**. Single-parity RAID-Z (raidz or raidz1) is similar to RAID-5. Double-parity RAID-Z (raidz2) is similar to RAID-6.

A RAID-Z configuration with N disks of size X with P parity disks can hold approximately `(N-P)*X` bytes and can withstand P device(s) failing before data integrity is compromised. You need at least two disks for a single-parity RAID-Z configuration and at least three disks for a double-parity RAID-Z configuration. For example, if you have three disks in a single-parity RAID-Z configuration, parity data occupies disk space equal to one of the three disks. Otherwise, no special hardware is required to create a RAID-Z configuration.

If you are creating a RAID-Z configuration with many disks, consider splitting the disks into multiple groupings. For example, a RAID-Z configuration with 14 disks is better split into two 7-disk groupings. **RAID-Z configurations with single-digit groupings of disks should perform better.**

---
## Scrubbing

The simplest way to check data integrity is to initiate an explicit scrubbing of all data within the pool. This operation traverses all the data in the pool once and verifies that all blocks can be read. Scrubbing proceeds as fast as the devices allow, though the priority of any I/O remains below that of normal operations. This operation might negatively impact performance, though the pool's data should remain usable and nearly as responsive while the scrubbing occurs.

**Scrub ZFS Pool:**
```bash
zpool scrub POOLNAME
```

**Example:**
```bash
zpool status -v POOLNAME

  pool: store
 state: ONLINE
  scan: scrub in progress since Fri Nov  4 06:43:51 2022
	317G scanned at 52.9G/s, 1.09M issued at 186K/s, 3.41T total
	0B repaired, 0.00% done, no estimated completion time
```

---
## Resilvering

When a device is replaced, a resilvering operation is initiated to move data from the good copies to the new device. This action is a form of disk scrubbing. Therefore, only one such action can occur at a given time in the pool. If a scrubbing operation is in progress, a resilvering operation suspends the current scrubbing and restarts it after the resilvering is completed.