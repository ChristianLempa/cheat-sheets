# Installing Docker on Various Linux Distributions

Docker is a popular containerization platform that allows you to package applications and their dependencies into containers. Here are the instructions for installing Docker on different Linux distributions:

## Ubuntu 20.04 and 22.04

```shell
# Update the package list
sudo apt update

# Install the required dependencies
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

# Add the Docker GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add the Docker repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update the package list again
sudo apt update

# Install Docker
sudo apt install -y docker-ce docker-ce-cli containerd.io

# Add your user to the docker group
sudo usermod -aG docker $USER

# Verify the installation
docker --version
```

## CentOS 8

```shell
# Install the required dependencies
sudo dnf install -y curl

# Set up the Docker repository
sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo

# Install Docker
sudo dnf install -y docker-ce docker-ce-cli containerd.io

# Start and enable Docker
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to the docker group
sudo usermod -aG docker $USER

# Verify the installation
docker --version
```

## Debian 10

```shell
# Update the package list
sudo apt update

# Install the required dependencies
sudo apt install -y apt-transport-https ca-certificates curl gnupg2 software-properties-common

# Add the Docker GPG key
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add the Docker repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update the package list again
sudo apt update

# Install Docker
sudo apt install -y docker-ce docker-ce-cli containerd.io

# Add your user to the docker group
sudo usermod -aG docker $USER

# Verify the installation
docker --version
```

## AlmaLinux 8

```shell
# Install the required dependencies
sudo dnf install -y curl

# Set up the Docker repository
sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo

# Install Docker
sudo dnf install -y docker-ce docker-ce-cli containerd.io

# Start and enable Docker
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to the docker group
sudo usermod -aG docker $USER

# Verify the installation
docker --version
```

## Fedora 34

```shell
# Install the required dependencies
sudo dnf install -y curl

# Set up the Docker repository
sudo dnf config-manager --add-repo=https://download.docker.com/linux/fed

ora/docker-ce.repo

# Install Docker
sudo dnf install -y docker-ce docker-ce-cli containerd.io

# Start and enable Docker
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to the docker group
sudo usermod -aG docker $USER

# Verify the installation
docker --version
```

That's it! You have successfully installed Docker on various Linux distributions. You can now use Docker to run and
