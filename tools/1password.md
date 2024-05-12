# 1Password Cheat-Sheet

## Account Management

| Command | Description |
| --- | --- |
| `op signin <account>` | Sign in to an account |
| `op signout` | Sign out of the current account |
| `op list accounts` | List all accounts |
| `op list accounts --all` | List all accounts, including archived |
| `op list accounts --vault <vault>` | List accounts in a specific vault |

## Item Management

| Command | Description |
| --- | --- |
| `op list items` | List all items |
| `op list items --vault <vault>` | List items in a specific vault |
| `op list items --tags <tag>` | List items with a specific tag |
| `op list items --category <category>` | List items in a specific category |
| `op list items --favorite` | List favorite items |
| `op create item <type>` | Create a new item |
| `op delete item <item>` | Delete an item |
| `op edit item <item>` | Edit an item |
| `op get item <item>` | Get the details of an item |
| `op get item <item> --fields <field_1>,<field_2>` | Get specific fields of an item |

## Vault Management

| Command | Description |
| --- | --- |
| `op create vault <vault>` | Create a new vault |
| `op delete vault <vault>` | Delete a vault |
| `op list vaults` | List all vaults |
| `op list vaults --all` | List all vaults, including archived |
