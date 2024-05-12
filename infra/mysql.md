# MySQL Cheat-Sheet

## Connect to MySQL

| Command | Description |
| --- | --- |
| `mysql -u root -p` | Connect to MySQL as root user |
| `mysql -u <user> -p` | Connect to MySQL as a specific user |
| `mysql -u root -p -h <host>` | Connect to MySQL on a specific host |

## Backup and Restore

| Command | Description |
| --- | --- |
| `mysqldump -u root -p <database> > backup.sql` | Backup a database to a file |
| `mysql -u root -p <database> < backup.sql` | Restore a database from a file |
