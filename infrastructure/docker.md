# Docker Cheat-Sheet
Docker is a set of platform as a service products that use OS-Level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries, and configuration files; they can communicate with each other through well-defined channels. Because all of the containers share the services of a single operating system kernel, they use fewer resources than virtual machines.

The service has both free and premium tiers. The software that hosts the containers is called **Docker Engine**.

## Container Management
COMMAND | DESCRIPTION
---|---
`docker create IMAGE` | Create a new container
`docker start CONTAINER` | Start a container
`docker stop CONTAINER` | Graceful stop a container
`docker kill CONTAINER` | Kill (SIGKILL) a container
`docker restart CONTAINER` | Graceful stop and restart a container
`docker pause CONTAINER` | Suspend a container
`docker unpause CONTAINER` | Resume a container
`docker rm CONTAINER` | Destroy a container
## Container Bulk Management
COMMAND | DESCRIPTION
---|---
`docker stop $(docker ps -q)` | To stop all the running containers
`docker stop $(docker ps -a -q)` | To stop all the stopped and running containers
`docker kill $(docker ps -q)` | To kill all the running containers
`docker kill $(docker ps -a -q)` | To kill all the stopped and running containers
`docker restart $(docker ps  -q)` | To restart all  running containers
`docker restart $(docker ps -a -q)` | To restart all the stopped and running containers
`docker rm $(docker ps  -q)` | To destroy all running containers
`docker rm $(docker ps -a -q)` | To destroy all the stopped and running containers
`docker pause $(docker ps  -q)` | To pause all  running containers
`docker pause $(docker ps -a -q)` | To pause all the stopped and running containers
`docker start $(docker ps  -q)` | To start all  running containers
`docker start $(docker ps -a -q)` | To start all the stopped and running containers
`docker rm -vf $(docker ps -a -q)` | To delete all containers including its volumes use
`docker rmi -f $(docker images -a -q)` | To delete all the images
### Parameters
COMMAND | DESCRIPTION
---|---
`docker run IMAGE` | Start a new container
`docker run --name CONTAINER IMAGE` | Start a new container and set a name
`docker run -p HOSTPORT:CONTAINERPORT IMAGE` | Start a new container with mapped ports
`docker run -P IMAGE` | Start a new container and map all ports
## Inspect
COMMAND | DESCRIPTION
---|---
`docker ps` | List running containers
`docker ps -a` | List all running containers
`docker logs CONTAINER` | Show a container output
`docker logs -f CONTAINER` | Follow a container output
`docker top CONTAINER` | List the processes running in a container
`docker diff` | Show the differences with the image (modified files)
`docker inspect` | Show information of a container (json formatted)
## Commands
COMMAND | DESCRIPTION
---|---
`docker attach CONTAINER` | Attach to a container
`docker cp CONTAINER:PATH HOSTPATH` | Copy files from the container
`docker cp HOSTPATH CONTAINER:PATH` | Copy files into the container
`docker export CONTAINER` | Export the content of the container (tar archive)
`docker exec CONTAINER` | Run a command inside a container
`docker exec -it CONTAINER /bin/bash` | Open an interactive shell inside a container
`docker wait CONTAINER` | Wait until the container terminates and return the exit code
## Images
COMMAND | DESCRIPTION
---|---
`docker images` | List all local images
`docker history IMAGE` | Show the image history
`docker inspect IMAGE` | Show information (json formatted)
`docker tag IMAGE TAG` | Tag an image
`docker commit CONTAINER IMAGE` | Create an image (from a container)
`docker import URL` | Create an image (from a tarball)
`docker rmi IMAGE` | Delete images
`docker pull REPO:[TAG]` | pull an image/repo from a registry
`docker push REPO:[TAG]` | push and image/repo to a registry
`docker search TEXT` | Search an image on the official registry
`docker login` | Login to a registry
`docker logout` | Logout from a registry
`docker save REPO:[TAG]` | Export an image/repo as a tarball
`docker load` | Load images from a tarball
## Volumes
COMMAND | DESCRIPTION
---|---
`docker volumes` | List all volumes
`docker volume create VOLUME` | Create a volume
`docker volume inspect VOLUME` | Show information (json formatted)
`docker volume rm VOLUME` | Destroy a volume
### Backup a container
Backup docker data from inside container volumes and package it in a tarball archive.
`docker run --rm --volumes-from CONTAINER -v $(pwd):/backup busybox tar cvfz /backup/backup.tar CONTAINERPATH`
### Restore container from backup
Restore the volume with a tarball archive.
`docker run --rm --volumes-from CONTAINER -v $(pwd):/backup busybox bash -c "cd CONTAINERPATH && tar xvf /backup/backup.tar --strip 1"`
## Networks

## Troubleshooting
### Networking
`docker run --name netshoot --rm -it nicolaka/netshoot /bin/bash`