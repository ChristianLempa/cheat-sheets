# MySQL Community Edition (CE) Cheat-Sheet

MySQL Community Edition is the freely downloadable version of the world's most popular open source database.

Project Homepage: [MySQL Community Edition](https://www.mysql.com/products/community/)
Documentation: [MySQL Docs](https://dev.mysql.com/doc/)

>_Editor's note:_ The MariaDB Project was forked from MySQL when [Sun Microsystems](https://en.wikipedia.org/wiki/Sun_Microsystems)' intellectual property [was acquired](https://en.wikipedia.org/wiki/Acquisition_of_Sun_Microsystems_by_Oracle_Corporation) by [Oracle](https://en.wikipedia.org/wiki/Oracle_Corporation).  MariaDB still shares enormous inter-compatibility with MySQL functions and software interoperability, and performance at most scales is arguably indiscernible from MySQL CE.  In this writers' opinion it is **not beneficial** in most cases to favor Oracle's monetized option over the GPL's MariaDB alternative.

---
## Installation

### Install MySQL on Debian/Ubuntu/Mint/Zorin/Deb forks

>[!warning]
> Common Debian repositories don't populate MySQL CE and require a vendor-provided repository available [here](https://dev.mysql.com/downloads/repo/apt/).  The repo file in this example is current as of 2024-01-20.
 
```bash
sudo apt update
sudo apt install -y lsb-release gnupg
wget https://dev.mysql.com/get/mysql-apt-config_0.8.29-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.29-1_all.deb
sudo mkdir /var/lib/mysql
sudo apt update
sudo apt install -y mysql-community-server mysql-common mycli --install-recommends
sudo mysql_secure_installation
```

### Install MySQL on RHEL/Fedora/CentOS/Alma/Rocky

```bash
sudo dnf update
sudo dnf install -y mysql-server mysql-common mycli
sudo mysql_secure_installation
```

### Install MySQL on Arch/Manjaro/Arco/ Arch forks

>[!warning]
> Common Arch repositories don't populate MySQL CE and the vendor doesn't provide one.  The packages are available in the [AUR](https://aur.archlinux.org/) but this is \***not recommended**\* for a production environment!!

##### Enable the AUR (if not already available)

>[!notice]
>_This **must** be done by a non-root user!_
```shell
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
##### Proceed with installation from the AUR

```bash
yay pacman -Syyu
yay -S mysql mysql-utilities mycli --noconfirm
sudo mysql_secure_installation
```

### Deploy MySQL in Docker
- [https://hub.docker.com/_/mysql/](https://hub.docker.com/_/mysql/)
- [https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/docker-mysql-getting-started.html](https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/docker-mysql-getting-started.html)

### Deploy MySQL in Kubernetes
- [https://dev.mysql.com/doc/mysql-operator/en/](https://dev.mysql.com/doc/mysql-operator/en/)
- [https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/](https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/)

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
