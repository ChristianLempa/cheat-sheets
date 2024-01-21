# Docker-Compose
...

## Networking
By default Docker-Compose will create a new network for the given compose file. You can change the behavior by defining custom networks in your compose file.
### Create and assign custom network
...
*Example:*
```yaml
networks:
  custom-network:

services:
  app:
    networks:
      - custom-network
```
### Use existing networks
If you want to use an existing Docker network for your compose files, you can add the `external: true` parameter in your compose file
*Example:*
```yaml
networks:
  existing-network:
    external: true
```

## Volumes
Volumes are data storage objects that Docker containers can use for persistent storage. 
### Create and map static volume(s)
```yaml
volumes:
  my-volume:

services:
  app:
    volumes:
      - my-volume:/path-in-container
```
These volumes are stored in `/var/lib/docker/volumes`.
### Create volume that is a CIFS mount to external share
```yaml
# Variables that will need to be changed:  
# <PUID> - User id for folder/file permissions  
# <PGID> - Group id for folder/file permissions  
# <PATH_TO_CONFIG> - Path where Unmanic will store config files  
# <PATH_TO_ENCODE_CACHE> - Cache path for in-progress encoding tasks  
# <REMOTE_IP> - Remote IP address of CIFS mount  
# <PATH_TO_LIBRARY> - Path in remote machine to be mounted as your library  
# <USERNAME> - Remote mount username  
# <PASSWORD> - Remote mount password  
#

---  
version: '2.4'  
services:  
  app:
    container_name: app_name  
    image: repo/app:tag  
    ports:  
      - 1234:1234
    environment:  
      - PUID=<PUID>  
      - PGID=<PGID>  
    volumes:
      - cifs_mount:/path-in-container

volumes:  
  cifs_mount:  
    driver: local  
    driver_opts:  
      type: cifs  
      device: //<REMOTE_IP>/<PATH_TO_LIBRARY>  
      o: "username=<USERNAME>,password=<PASSWORD>,vers=3.0,uid=<PUID>,gid=<PGID>"
```
