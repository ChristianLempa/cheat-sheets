# Ethtool Cheat-Sheet

## Displaying Information

| Command | Description |
| --- | --- |
| `ethtool INTERFACE` | Display information about a specific network interface |
| `ethtool -i INTERFACE` | Display driver information |
| `ethtool -a INTERFACE` | Display all settings |
| `ethtool -k INTERFACE` | Display offload settings |
| `ethtool -c INTERFACE` | Display coalescing settings |
| `ethtool -g INTERFACE` | Display ring buffer settings |
| `ethtool -l INTERFACE` | Display large receive offload settings |
| `ethtool -S INTERFACE` | Display statistics |
| `ethtool -t INTERFACE` | Test the network interface for offloading capabilities |
| `ethtool -T INTERFACE` | Display time stamping settings |
| `ethtool -x INTERFACE` | Display channel settings |
| `ethtool -P INTERFACE` | Display permanent MAC address |
| `ethtool -N INTERFACE` | Display offload settings |
| `ethtool -u INTERFACE` | Display bus information |
| `ethtool -d INTERFACE` | Display register dump |
| `ethtool -g INTERFACE` | Display ring buffer settings |

## Setting Parameters

| Command | Description |
| --- | --- |
| `ethtool -G INTERFACE` | Set ring buffer settings |
| `ethtool -L INTERFACE` | Set large receive offload settings |
| `ethtool -A INTERFACE` | Set pause parameters |
| `ethtool -C INTERFACE` | Set coalescing settings |
| `ethtool -K INTERFACE` | Set offload settings |
| `ethtool -N INTERFACE` | Set offload settings |
| `ethtool -p INTERFACE` | Blink the LED on the network interface |
| `ethtool -r INTERFACE` | Reset the network interface |
