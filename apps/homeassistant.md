# Homeassistant

Home Assistant is an open-source home automation platform that allows you to control and automate various smart devices in your home. It integrates with a wide range of devices and services, and provides a centralized interface for managing your home automation system.

With Home Assistant, you can create complex automation routines, set up voice control with popular virtual assistants, and monitor your home’s energy usage and other statistics.


## Installation

> Home Assistant offers four installation methods, with the recommended methods being the Home Assistant Operating System and Home Assistant Container. *This documentation only covers the Home Assistant Container installation method on an x86-64 PC.*

### Compose Template

```yaml
---
services:
  homeassistant:
    container_name: homeassistant
    image: "ghcr.io/home-assistant/home-assistant:stable"
    volumes:
      - /PATH_TO_YOUR_CONFIG:/config
      - /etc/localtime:/etc/localtime:ro
    restart: unless-stopped
    privileged: true
    network_mode: host
```


### Exposing Devices

In order to use Zigbee or other integrations that require access to devices, you need to map the appropriate device into the container. Ensure the user that is running the container has the correct privileges to access the `/dev/tty*` file, then add the device mapping to your container instructions:

```yaml
---
services:
  homeassistant:
    ...
    devices:
      - /dev/ttyUSB0:/dev/ttyUSB0
```


## Configuration

Work in Progress

