# Civo

## Instances

| Command | Description |
| --- | --- |
| `civo instance ls` | List instances |
| `civo instance show ID` | Show instance details |
| `civo instance create HOSTNAME [flags]` | Create a new instance |
| `civo instance firewall HOSTNAME FIREWALL` | Set firewall for instance |
| `civo instance password [flags]` | Show instance's default password |
| `civo instance public-ip [flags]` | Enable/disable controls if instance should have a public IP |
| `civo instance reboot HOSTNAME` | Hard reboot an instance |
| `civo instance remove HOSTNAME` | Remove/delete instance |
| `civo instance size` | List instances size |
| `civo instance soft-reboot` | Soft reboot an instance |
| `civo instance start` | Start an instance |
| `civo instance stop` | Stop an instance |
| `civo instance tag` | Change the instance's tags |
| `civo instance update` | Change the instance |
| `civo instance upgrade` | Upgrade an instance |

### Instance Creation Flags

| Flag | Description |
| --- | --- |
| `--size`, `-i` | Size of the instance |
| `--diskimage`, `-t` | Disk image to use |
| `--public-ip`, `-p` | Enable a public IP |
| `--firewall`, `-l` | Firewall to apply |
| `--region` | Region to create the instance in |
| `--ssh-key`, `-k` | SSH key to add to the instance |
| `--wait`, `-w` | Wait for the instance to be created |

## Query Disk Images and Sizes

| Command | Description |
| --- | --- |
| `civo diskimage ls` | List disk images |
| `civo diskimage find STRING` | Find disk images by name |
| `civo size ls` | List sizes |
