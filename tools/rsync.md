# rsync cheatsheet

***rsync*** is a utility for efficiently transferring and synchronizing files between a computer and a storage drive and across networked computers by comparing the modification times and sizes of files. It is commonly found on Unix-like operating systems and is under the GPL-3.0-or-later license.

Rsync is written in C as a single threaded application. The rsync algorithm is a type of delta encoding, and is used for minimizing network usage. Zlib may be used for additional data compression, and SSH or stunnel can be used for security. Rsync is the facility typically used for synchronizing software repositories on mirror sites used by package management systems.

Rsync is typically used for synchronizing files and directories between two different systems. For example, if the command rsync local-file user@remote-host:remote-file is run, rsync will use SSH to connect as user to remote-host. Once connected, it will invoke the remote host's rsync and then the two programs will determine what parts of the local file need to be transferred so that the remote file matches the local one.

Rsync can also operate in a daemon mode (rsyncd), serving and receiving files in the native rsync protocol (using the "rsync://" syntax).

## Sync folder in-progress to final

```
rsync -avz ./in-progress /final
```

## Sync the content from in-progress to final

```
rsync -avz ./in-progress/ /final
```

## Sync the content from in-progress to final and exclude the contents from in-progress/junk/

```
rsync -avz --exclude=junk/* ./in-progress/ /final
```

## Rsync over SSH

```
rsync -avz /var/www/ user@1.2.3.4:/var/www/
```

## More examples
- [resource](https://devhints.io/rsync)
