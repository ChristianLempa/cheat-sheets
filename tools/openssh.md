# OpenSSH Cheat-Sheet

## Known Hosts

Remove Entry from the Known-Hosts File.
```bash
ssh-keygen -R hostname
```

## Using the SSH Config File
If you are regularly connecting to multiple remote systems over SSH, you can configure your remote servers with the `.ssh/config` file.

**Example:***
```ini
Host dev
    HostName dev.your-domain
    User xcad
	Port 7654
    IdentityFile ~/.ssh/targaryen.key

Host *
    User root
    Compression yes
```

Connect to a host (like *dev* , eg.) with `ssh dev`.
[[linux]]
