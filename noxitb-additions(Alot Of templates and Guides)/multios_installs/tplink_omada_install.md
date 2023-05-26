# Installing Omada Controller on Various Linux Distributions

Omada Controller is a software application that allows centralized management of TP-Link Omada devices, such as access points, switches, and gateways. It provides a user-friendly interface for configuring and monitoring your network. Here are the instructions for installing Omada Controller on different Linux distributions:

**Note: Please make sure to check the TP-Link Omada website for the latest version of Omada Controller before proceeding with the installation.**

## Ubuntu 20.04 and 22.04

```shell
# Update the package list
sudo apt update

# Install the required dependencies
sudo apt install -y openjdk-11-jre-headless unzip

# Download the Omada Controller package (replace <latest_version> with the actual version)
wget https://static.tp-link.com/upload/software/2023/202303/20230321/Omada_SDN_Controller_v<latest_version>_Linux_x64.deb

# Install the Omada Controller package
sudo dpkg -i Omada_SDN_Controller_v<latest_version>_Linux_x64.deb

# Start the Omada Controller service
sudo systemctl start omada

# Enable the Omada Controller service to start on boot
sudo systemctl enable omada

# Access the Omada Controller web interface
# Visit http://localhost:8088 in your web browser
```

## CentOS 8

```shell
# Update the package list
sudo dnf update -y

# Install the required dependencies
sudo dnf install -y java-11-openjdk-headless unzip

# Download the Omada Controller package (replace <latest_version> with the actual version)
wget https://static.tp-link.com/upload/software/2023/202303/20230321/Omada_SDN_Controller_v<latest_version>_Linux_x64.rpm

# Install the Omada Controller package
sudo rpm -i Omada_SDN_Controller_v<latest_version>_Linux_x64.rpm

# Start the Omada Controller service
sudo systemctl start omada

# Enable the Omada Controller service to start on boot
sudo systemctl enable omada

# Access the Omada Controller web interface
# Visit http://localhost:8088 in your web browser
```

## Debian 10

```shell
# Update the package list
sudo apt update

# Install the required dependencies
sudo apt install -y openjdk-11-jre-headless unzip

# Download the Omada Controller package (replace <latest_version> with the actual version)
wget https://static.tp-link.com/upload/software/2023/202303/20230321/Omada_SDN_Controller_v<latest_version>_Linux_x64.deb

# Install the Omada Controller package
sudo dpkg -i Omada_SDN_Controller_v<latest_version>_Linux_x64.deb

# Start the Omada Controller service
sudo systemctl start omada

# Enable the Omada Controller service to start on boot
sudo systemctl enable omada

# Access the Omada Controller web interface
# Visit http://localhost:8088 in your web browser
```

That's it! You have successfully installed the latest version of Omada Controller on various Linux distributions. You can now configure and manage your TP-Link Omada network devices using the web interface.

Please note that this guide provides a general overview of the installation process and assumes you have a basic understanding of Linux package management. Make sure to review the specific documentation for each distribution and check the TP-Link Omada website for any distribution-specific instructions or troubleshooting steps
