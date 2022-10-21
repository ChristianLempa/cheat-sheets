# SSH Keygen Cheatsheet

***ssh-keygen*** is a standard component of the Secure Shell ([SSH](ssh.md)) protocol suite found on Unix, Unix-like and Microsoft Windows computer systems used to establish secure shell sessions between remote computers over insecure networks, through the use of various cryptographic techniques. The *ssh-keygen* utility is used to generate, manage, and convert authentication keys.

## Usage

Create a SSH Private Key:

```
ssh-keygen -f ~/.ssh/mykey -t rsa -C "MyKey" -q -N ""
```

Generate a SSH Public Key from a Private Key:

```
ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
```

Convert a multiline (newline) public ssh key to a normal public key:

```
ssh-keygen -i -f ~/Downloads/key.multiline_pub > ~/Downloads/key.pub
```

View the Public SSH Key from a Private Key:

```
ssh-keygen -y -f ~/.ssh/id_rsa
```

## See also

- [ssh](ssh.md)
