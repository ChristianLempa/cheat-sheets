# SSH Cheat Sheet

| Command                                               | Description                                                          |
| ----------------------------------------------------- | -------------------------------------------------------------------- |
| `ssh user@host`                                       | Connect to a remote host as a specified user.                        |
| `ssh -p port user@host`                               | Connect to a remote host on a specified port.                        |
| `ssh -i /path/to/key user@host`                       | Connect using a specific private key for authentication.             |
| `ssh user@host 'command'`                             | Execute a command on the remote host without an interactive session. |
| `scp source user@host:/path`                          | Securely copy files from local to remote.                            |
| `scp user@host:/path/to/file .`                       | Securely copy files from remote to local.                            |
| `sftp user@host`                                      | Start an SFTP session for file transfers.                            |
| `ssh-keygen`                                          | Generate a new SSH key pair.                                         |
| `ssh-copy-id user@host`                               | Install your public key on a remote host for password-less login.    |
| `ssh -L local_port:remote_host:remote_port user@host` | Set up local port forwarding.                                        |
| `ssh -R remote_port:local_host:local_port user@host`  | Set up remote port forwarding.                                       |
| `ssh -D local_port user@host`                         | Set up a SOCKS proxy on the local port.                              |
| `ssh -v user@host`                                    | Enable verbose mode for debugging SSH connection issues.             |
| `ssh -X user@host`                                    | Enable X11 forwarding for graphical applications.                    |
| `ssh -C user@host`                                    | Enable compression for the SSH session.                              |
| `ssh-add /path/to/key`                                | Add a private key to the SSH authentication agent.                   |
| `ssh-agent`                                           | Start the SSH authentication agent.                                  |
| `ssh config`                                          | Edit SSH client configuration file (typically `~/.ssh/config`).      |
