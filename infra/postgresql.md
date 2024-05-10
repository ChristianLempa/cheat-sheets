# PostgreSQL Cheat-Sheet

## Connect to PostgreSQL

| Command | Description |
| --- | --- |
| `psql -U postgres` | Connect to PostgreSQL as the `postgres` user |
| `psql -U USER -d DBNAME` | Connect to PostgreSQL as a specific user and database |
| `psql -U USER -d DBNAME -h HOST` | Connect to PostgreSQL on a specific host |

## PostreSQL CLI Commands

| Command | Description |
| --- | --- |
| `\c DBNAME` | Connect to a specific database |
| `\password USERNAME` | Change password for a specific user |
| `\l` | List all databases |
| `\d+` | Show detailed information about various database objects |
| `\dt` | List all tables in the current database |
| `\du` | List all users |
| `\df` | List all functions |
| `\dv` | List all views |
| `\dn` | List all schemas |
| `\dp` | List all permissions |
| `\di` | List all indexes |
| `\ds` | List all sequences |
| `\d+` | Show detailed information about various database objects |
| `\q` | Quit psql |
| `\x` | Toggle expanded output |

## Backup and Restore

| Command | Description |
| --- | --- |
| `pg_dump DBNAME > backup.sql` | Backup a database to a file |
| `psql DBNAME < backup.sql` | Restore a database from a file |
