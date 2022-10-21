# Sudo Cheatsheet

***sudo*** is a program for Unix-like computer operating systems that enables users to run programs with the security privileges of another user, by default the superuser. It originally stood for "superuser do", as that was all it did, and it is its most common usage; however, the official Sudo project page lists it as "su do". The current [Linux](linux.md) manual pages for *su* defines it as "substitute user", making the correct meaning of sudo "substitute user, do", because *sudo* can run a command as other users as well.

Unlike the similar command *su*, users must, by default, supply their own password for authentication, rather than the password of the target user. After authentication, and if the configuration file (typically /etc/sudoers) permits the user access, the system invokes the requested command. The configuration file offers detailed access permissions, including enabling commands only from the invoking terminal; requiring a password per user or group; requiring re-entry of a password every time or never requiring a password at all for a particular command line. It can also be configured to permit passing arguments or multiple commands.

## Usage

User to sudo without a password:

```
echo "${USER} ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/no-sudo-password-for-${USER}
```

Run a command as a user:

```
sudo -H -u ubuntu bash -c 'echo "I am: $USER"' 
```
