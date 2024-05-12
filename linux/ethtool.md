# Ethtool Cheat-Sheet

## Displaying Information

| Command | Description |
| --- | --- |
| `ethtool <interface>` | Display information about a specific network interface |
| `ethtool -i <interface>` | Display driver information |
| `ethtool -a <interface>` | Display all settings |
| `ethtool -k <interface>` | Display offload settings |
| `ethtool -c <interface>` | Display coalescing settings |
| `ethtool -g <interface>` | Display ring buffer settings |
| `ethtool -l <interface>` | Display large receive offload settings |
| `ethtool -S <interface>` | Display statistics |
| `ethtool -t <interface>` | Test the network interface for offloading capabilities |
| `ethtool -T <interface>` | Display time stamping settings |
| `ethtool -x <interface>` | Display channel settings |
| `ethtool -P <interface>` | Display permanent MAC address |
| `ethtool -N <interface>` | Display offload settings |
| `ethtool -u <interface>` | Display bus information |
| `ethtool -d <interface>` | Display register dump |
| `ethtool -g <interface>` | Display ring buffer settings |

## Setting Parameters

| Command | Description |
| --- | --- |
| `ethtool -G <interface>` | Set ring buffer settings |
| `ethtool -L <interface>` | Set large receive offload settings |
| `ethtool -A <interface>` | Set pause parameters |
| `ethtool -C <interface>` | Set coalescing settings |
| `ethtool -K <interface>` | Set offload settings |
| `ethtool -N <interface>` | Set offload settings |
| `ethtool -p <interface>` | Blink the LED on the network interface |
| `ethtool -r <interface>` | Reset the network interface |
