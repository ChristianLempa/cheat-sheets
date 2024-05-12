# SQLite Cheat-Sheet

## Connect to SQLite

| Command | Description |
| --- | --- |
| `sqlite3 <db>` | Connect to a SQLite database |

## SQLite CLI Commands

| Command | Description |
| --- | --- |
| `.databases` | List all databases |
| `.tables` | List all tables in the current database |
| `.schema <table>` | Show the schema of a table |
| `.indexes <table>` | List all indexes in a table |
| `.show` | Show the current settings |
| `.help` | Show help information |
| `.shell <command` | Run a shell command |
| `.exit` | Quit SQLite |

## Backup and Restore

| Command | Description |
| --- | --- |
| `.backup <file>` | Backup the current database to a file |
| `.restore <file>` | Restore a database from a file |
| `.dump` | Dump the database as SQL statements |
