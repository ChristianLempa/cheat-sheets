# MySQL Cheat-Sheet

## Connect to MySQL

| Command | Description |
| --- | --- |
| `mysql -u root -p` | Connect to MySQL as root user |
| `mysql -u USER -p` | Connect to MySQL as a specific user |
| `mysql -u root -p -h HOST` | Connect to MySQL on a specific host |

## Backup and Restore

| Command | Description |
| --- | --- |
| `mysqldump -u root -p DBNAME > backup.sql` | Backup a database to a file |
| `mysql -u root -p DBNAME < backup.sql` | Restore a database from a file |
