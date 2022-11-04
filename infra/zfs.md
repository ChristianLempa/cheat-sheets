WIP

Reference: [Oracle Solaris ZFS Administration Guide](https://docs.oracle.com/cd/E19253-01/819-5461/index.html)

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