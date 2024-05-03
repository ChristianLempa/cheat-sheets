# ZFS Cheat-Sheet

## File System Management

| Command | Description |
| --- | --- |
| `zfs list` | List ZFS file systems |
| `zfs create POOLNAME/FS` | Create a ZFS file system |
| `zfs set PROPERTY=VALUE POOLNAME/FS` | Set ZFS file system properties |
| `zfs get PROPERTY POOLNAME/FS` | Get ZFS file system properties |
| `zfs destroy POOLNAME/FS` | Destroy a ZFS file system |

## Pool Management

| Command | Description |
| --- | --- |
| `zpool list` | List ZFS pools |
| `zpool create POOLNAME DEVICE` | Create a ZFS pool |
| `zpool destroy POOLNAME` | Destroy a ZFS pool |
| `zpool iostat` | Display ZFS pool I/O statistics |
| `zpool status` | Display ZFS pool status |
| `zpool history` | Display ZFS pool history |
| `zpool events` | Display ZFS pool events |
| `zpool scrub POOLNAME` | Scrub a ZFS pool |
| `zpool clear POOLNAME` | Clear ZFS pool errors |
| `zpool trim POOLNAME` | Trim a ZFS pool |
| `zpool add POOLNAME DEVICE` | Add a device to a ZFS pool |
| `zpool remove POOLNAME DEVICE` | Remove a device from a ZFS pool |
| `zpool replace POOLNAME DEVICE` | Replace a device in a ZFS pool |
| `zpool offline POOLNAME DEVICE` | Offline a device in a ZFS pool |

## Snapshots

| Command | Description |
| --- | --- |
| `zfs list -t snapshot` | List ZFS snapshots |
| `zfs snapshot POOLNAME/FS@SNAPSHOT` | Create a ZFS snapshot |
| `zfs rollback POOLNAME/FS@SNAPSHOT` | Rollback a ZFS snapshot |
| `zfs diff POOLNAME/FS@SNAPSHOT1 POOLNAME/FS@SNAPSHOT2` | Compare ZFS snapshots |
| `zfs send POOLNAME/FS@SNAPSHOT` | Send ZFS snapshots |
| `zfs receive POOLNAME/FS` | Receive ZFS snapshots |

## Clones

| Command | Description |
| --- | --- |
| `zfs clone POOLNAME/FS@SNAPSHOT POOLNAME/FS` | Create a ZFS clone |
| `zfs promote POOLNAME/FS` | Promote a ZFS clone |
| `zfs rollback POOLNAME/FS` | Rollback a ZFS clone |
| `zfs destroy POOLNAME/FS` | Destroy a ZFS clone |
