# MariaDB Cheat-Sheet

## Install MariaDB on Ubuntu 20.04 LTS
```bash
sudo apt update
sudo apt install mariadb-server
sudo mysql_secure_installation
```

## Access Database from outside
Open `/etc/mysql/mariadb.conf.d/50-server.cnf` and change the `bind-address` to:
```
...

bind-address = 0.0.0.0

...
```
## Create Administrative User
1. Create a new user `newuser` for the host `localhost` with a new `password`:
```mysql
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```

2. Grant all permissions to the new user
```mysql
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
``` 

3. Update permissions
```mysql
FLUSH PRIVILEGES;
```
