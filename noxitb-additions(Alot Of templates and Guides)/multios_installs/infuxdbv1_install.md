# Installing InfluxDB on Various Linux Distributions

InfluxDB is a popular open-source time series database that is designed to handle high write and query loads. It is commonly used for storing and analyzing time series data. Here are the instructions for installing InfluxDB on different Linux distributions:

## Ubuntu 20.04 and 22.04

```shell
# Import the InfluxDB GPG key
wget -qO- https://repos.influxdata.com/influxdb.key | sudo apt-key add -

# Add the InfluxDB repository
echo "deb https://repos.influxdata.com/ubuntu focal stable" | sudo tee /etc/apt/sources.list.d/influxdb.list

# Update the package list
sudo apt update

# Install InfluxDB
sudo apt install -y influxdb

# Start the InfluxDB service
sudo systemctl start influxdb

# Enable the InfluxDB service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB web interface
# Visit http://localhost:8086 in your web browser
```

## CentOS 8

```shell
# Download the InfluxDB repository configuration package
sudo dnf install -y wget
sudo wget https://repos.influxdata.com/influxdb.key -O /etc/pki/rpm-gpg/RPM-GPG-KEY-influxdata

# Add the InfluxDB repository
echo "[influxdb]" | sudo tee /etc/yum.repos.d/influxdb.repo
echo "name = InfluxDB Repository" | sudo tee -a /etc/yum.repos.d/influxdb.repo
echo "baseurl = https://repos.influxdata.com/rhel/8/x86_64/stable/" | sudo tee -a /etc/yum.repos.d/influxdb.repo
echo "gpgcheck = 1" | sudo tee -a /etc/yum.repos.d/influxdb.repo
echo "gpgkey = file:///etc/pki/rpm-gpg/RPM-GPG-KEY-influxdata" | sudo tee -a /etc/yum.repos.d/influxdb.repo

# Install InfluxDB
sudo dnf install -y influxdb

# Start the InfluxDB service
sudo systemctl start influxdb

# Enable the InfluxDB service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB web interface
# Visit http://localhost:8086 in your web browser
```

## Debian 10

```shell
# Import the InfluxDB GPG key
wget -qO- https://repos.influxdata.com/influxdb.key | sudo apt-key add -

# Add the InfluxDB repository
echo "deb https://repos.influxdata.com/debian buster stable" | sudo tee /etc/apt/sources.list.d/influxdb.list

# Update the package list
sudo apt update

# Install InfluxDB
sudo apt install -y influxdb

# Start the InfluxDB service
sudo systemctl start influxdb

# Enable the InfluxDB service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB web interface
# Visit http://localhost:8086 in your web browser
```

## AlmaLinux 8

```shell
# Download the InfluxDB repository configuration package
sudo dnf install -y wget
sudo wget https://repos.influxdata.com/influxdb.key -O /etc/pki/rpm-gpg/RPM-GPG-KEY-influxdata



# Add the InfluxDB repository
echo "[influxdb]" | sudo tee /etc/yum.repos.d/influxdb.repo
echo "name = InfluxDB Repository" | sudo tee -a /etc/yum.repos.d/influxdb.repo
echo "baseurl = https://repos.influxdata.com/rhel/8/x86_64/stable/" | sudo tee -a /etc/yum.repos.d/influxdb.repo
echo "gpgcheck = 1" | sudo tee -a /etc/yum.repos.d/influxdb.repo
echo "gpgkey = file:///etc/pki/rpm-gpg/RPM-GPG-KEY-influxdata" | sudo tee -a /etc/yum.repos.d/influxdb.repo

# Install InfluxDB
sudo dnf install -y influxdb

# Start the InfluxDB service
sudo systemctl start influxdb

# Enable the InfluxDB service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB web interface
# Visit http://localhost:8086 in your web browser
```

That's it! You have successfully installed InfluxDB on various Linux distributions. You can now start using InfluxDB to store and query time series data.

Please note that this guide provides a general overview of the installation process and assumes you have a basic understanding of Linux package management. Make sure to review the specific documentation for each distribution for any distribution-specific instructions or troubleshooting steps.
