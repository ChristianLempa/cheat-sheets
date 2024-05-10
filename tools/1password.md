# 1Password Cheat-Sheet

## Account Management

| Command | Description |
| --- | --- |
| `op signin ACCOUNT` | Sign in to an account |
| `op signout` | Sign out of the current account |
| `op list accounts` | List all accounts |
| `op list accounts --all` | List all accounts, including archived |
| `op list accounts --vault VAULT` | List accounts in a specific vault |

## Item Management

| Command | Description |
| --- | --- |
| `op list items` | List all items |
| `op list items --vault VAULT` | List items in a specific vault |
| `op list items --tags TAG` | List items with a specific tag |
| `op list items --category CATEGORY` | List items in a specific category |
| `op list items --favorite` | List favorite items |
| `op create item TYPE` | Create a new item |
| `op delete item ITEM` | Delete an item |
| `op edit item ITEM` | Edit an item |
| `op get item ITEM` | Get the details of an item |
| `op get item ITEM --fields FIELD1,FIELD2` | Get specific fields of an item |

## Vault Management

| Command | Description |
| --- | --- |
| `op create vault VAULT` | Create a new vault |
| `op delete vault VAULT` | Delete a vault |
| `op list vaults` | List all vaults |
| `op list vaults --all` | List all vaults, including archived |
