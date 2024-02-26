# Installing InfluxDB 2.x on Various Linux Distributions

InfluxDB 2.x is a powerful time series database designed to handle high write and query loads. It introduces a new architecture and API compared to InfluxDB 1.x. Here are the instructions for installing InfluxDB 2.x on different Linux distributions:

## Ubuntu 20.04 and 22.04

```shell
# Download and install the InfluxDB 2.x package
wget https://dl.influxdata.com/influxdb/releases/influxdb2_2.0.8_amd64.deb
sudo dpkg -i influxdb2_2.0.8_amd64.deb

# Start the InfluxDB 2.x service
sudo systemctl start influxdb

# Enable the InfluxDB 2.x service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB 2.x web interface
# Visit http://localhost:8086 in your web browser
```

## CentOS 8

```shell
# Download and install the InfluxDB 2.x package
wget https://dl.influxdata.com/influxdb/releases/influxdb2-2.0.8.x86_64.rpm
sudo rpm -ivh influxdb2-2.0.8.x86_64.rpm

# Start the InfluxDB 2.x service
sudo systemctl start influxdb

# Enable the InfluxDB 2.x service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB 2.x web interface
# Visit http://localhost:8086 in your web browser
```

## Debian 10

```shell
# Download and install the InfluxDB 2.x package
wget https://dl.influxdata.com/influxdb/releases/influxdb2_2.0.8_amd64.deb
sudo dpkg -i influxdb2_2.0.8_amd64.deb

# Start the InfluxDB 2.x service
sudo systemctl start influxdb

# Enable the InfluxDB 2.x service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB 2.x web interface
# Visit http://localhost:8086 in your web browser
```

## AlmaLinux 8

```shell
# Download and install the InfluxDB 2.x package
wget https://dl.influxdata.com/influxdb/releases/influxdb2-2.0.8.x86_64.rpm
sudo rpm -ivh influxdb2-2.0.8.x86_64.rpm

# Start the InfluxDB 2.x service
sudo systemctl start influxdb

# Enable the InfluxDB 2.x service to start on boot
sudo systemctl enable influxdb

# Access the InfluxDB 2.x web interface
# Visit http://localhost:8086 in your web browser
```

That's it! You have successfully installed InfluxDB version 2.x on various Linux distributions. You can now start using InfluxDB to store and query time series data.

Please note that this guide provides a general overview of the installation process and assumes you have a basic understanding of Linux package management. Make sure to review the specific documentation for each distribution for any distribution-specific instructions or troubleshooting steps.

```

```
