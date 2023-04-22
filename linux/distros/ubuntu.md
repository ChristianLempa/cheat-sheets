# Ubuntu

Ubuntu is a Linux distribution based on Debian and composed mostly of free and open-source software.Ubuntu is officially released in three editions: Desktop, Server, and Core for Internet of things devices and robots. Ubuntu is a popular operating system for cloud computing, with support for OpenStack.

## How to enable sudo without a password for a user

Open a Terminal window and type:

```
sudo visudo
```

In the bottom of the file, add the following line:

```
$USER ALL=(ALL) NOPASSWD: ALL
```

Where `$USER` is your username on your system. Save and close the sudoers file (if you haven't changed your default terminal editor (you'll know if you have), press Ctl + x to exit `nano` and it'll prompt you to save).