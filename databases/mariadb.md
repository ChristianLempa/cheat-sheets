# MariaDB Cheat-Sheet

MariaDB Server is one of the most popular open source relational databases. It’s made by the original developers of MySQL and guaranteed to stay open source. It is part of most cloud offerings and the default in most Linux distributions.

It is built upon the values of performance, stability, and openness, and MariaDB Foundation ensures contributions will be accepted on technical merit. Recent new functionality includes advanced clustering with Galera Cluster 4, compatibility features with Oracle Database and Temporal Data Tables, allowing one to query the data as it stood at any point in the past.

Project Homepage: [MariaDB](https://mariadb.org/)
Documentation: [MariaDB Docs](https://mariadb.org/documentation/)

---
## Installation

### Install MariaDB on Debian/Ubuntu/Mint/Zorin/forks

```bash
sudo apt update
sudo apt install -y mariadb-server mycli --install-recommends
sudo mysql_secure_installation
```

### Install MariaDB on RHEL/Fedora/CentOS/Alma/Rocky

```bash
sudo dnf update
sudo dnf install -y mariadb-server mycli
sudo mysql_secure_installation
```

### Install MariaDB on Arch/Manjaro/Arco/forks

```bash
sudo pacman -Syyu
sudo pacman -S mariadb-server mycli --noconfirm
sudo mysql_secure_installation
```

### Deploy MariaDB in Docker
- [https://hub.docker.com/_/mariadb](https://hub.docker.com/_/mariadb)
- [https://docs.linuxserver.io/images/docker-mariadb/](https://docs.linuxserver.io/images/docker-mariadb/)

### Deploy MariaDB in Kubernetes
- [https://mariadb.org/start-mariadb-in-k8s/](https://mariadb.org/start-mariadb-in-k8s/)
- [https://kubedb.com/kubernetes/databases/run-and-manage-mariadb-on-kubernetes/](https://kubedb.com/kubernetes/databases/run-and-manage-mariadb-on-kubernetes/)

## Access Database from outside

Open `/etc/mysql/mariadb.conf.d/50-server.cnf` and change the line containing `bind-address` to `bind-address = 0.0.0.0`.

---
## Create Administrative User

Access the MySQL command line by entering `mysql -u root -p` in the shell followed by the Database `root` password.

Create a new user `newuser` for the host `localhost` with a new `password`:

```sql
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```

Grant all permissions to the new user

```sql
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
```

Update permissions

```sql
FLUSH PRIVILEGES
```
