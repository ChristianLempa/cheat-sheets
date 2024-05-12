# ZFS Cheat-Sheet

## File System Management

| Command | Description |
| --- | --- |
| `zfs list` | List ZFS file systems |
| `zfs create <pool>/<filesystem>` | Create a ZFS file system |
| `zfs set <property>=<value> <pool>/<filesystem>` | Set ZFS file system properties |
| `zfs get <property> <pool>/<filesystem>` | Get ZFS file system properties |
| `zfs destroy <pool>/<filesystem>` | Destroy a ZFS file system |

## Pool Management

| Command | Description |
| --- | --- |
| `zpool list` | List ZFS pools |
| `zpool create <pool> <device>` | Create a ZFS pool |
| `zpool destroy <pool>` | Destroy a ZFS pool |
| `zpool iostat` | Display ZFS pool I/O statistics |
| `zpool status` | Display ZFS pool status |
| `zpool history` | Display ZFS pool history |
| `zpool events` | Display ZFS pool events |
| `zpool scrub <pool>` | Scrub a ZFS pool |
| `zpool clear <pool>` | Clear ZFS pool errors |
| `zpool trim <pool>` | Trim a ZFS pool |
| `zpool add <pool> <device>` | Add a device to a ZFS pool |
| `zpool remove <pool> <device>` | Remove a device from a ZFS pool |
| `zpool replace <pool> <device>` | Replace a device in a ZFS pool |
| `zpool offline <pool> <device>` | Offline a device in a ZFS pool |

## Snapshots

| Command | Description |
| --- | --- |
| `zfs list -t snapshot` | List ZFS snapshots |
| `zfs snapshot <pool>/<filesystem>@<snapshot>` | Create a ZFS snapshot |
| `zfs rollback <pool>/<filesystem>@<snapshot>` | Rollback a ZFS snapshot |
| `zfs diff <pool>/<filesystem>@<snapshot_1> <pool>/<filesystem>@<snapshot_2>` | Compare ZFS snapshots |
| `zfs send <pool>/<filesystem>@<snapshot>` | Send ZFS snapshots |
| `zfs receive <pool>/<filesystem>` | Receive ZFS snapshots |

## Clones

| Command | Description |
| --- | --- |
| `zfs clone <pool>/<filesystem>@<snapshot> <pool>/<filesystem>` | Create a ZFS clone |
| `zfs promote <pool>/<filesystem>` | Promote a ZFS clone |
| `zfs rollback <pool>/<filesystem>` | Rollback a ZFS clone |
| `zfs destroy <pool>/<filesystem>` | Destroy a ZFS clone |
