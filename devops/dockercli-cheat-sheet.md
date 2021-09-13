# Docker CLI Cheat-Sheet
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


