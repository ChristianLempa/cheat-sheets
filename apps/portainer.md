# Portainer
Easily deploy, configure and secure containers in minutes on [Docker](docker/docker.md), [Kubernetes](kubernetes/kubernetes.md), Swarm and Nomad in any cloud, datacenter or device.

Project Homepage: [Portainer](https://www.portainer.io)
Documentation: [Portainer Docs](http://documentation.portainer.io)

---

## Installation
There are two installation options: [Portainer CE](https://docs.portainer.io/start/install-ce/server/docker) (Community Edition)  and [Portainer BE](https://docs.portainer.io/start/install/server/docker) (Business Edition).  Up to three nodes of BE can be requested at no cost; documentation outlining the feature differences between BE and CE [here](https://docs.portainer.io/).


>**Preparation**
*[[docker|Docker]]*, *[[Docker Swarm|Docker Swarm]]*, or *[[kubernetes|Kubernetes]]* must be installed to run Portainer.  *Docker-compose* is also recommended but not required; [[docker-compose|documented here]].


The examples below focus on installing Community Edition (CE) on Linux but Windows and Windows Container Service installation instructions (very little, if any, difference) can also be accessed from the hyperlinks above.

## Deploy Portainer CE in Docker on Linux
1) Create the volume that Portainer Server will use to store its database:
		```docker volume create portainer_data```
2) Download and install the Portainer Server container:
		```docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest```
3) Check to see whether the Portainer Server container has started by running `docker ps`
		*Example response showing active service:*
		`root@server:~# docker ps`		
		`CONTAINER_IMAGE`                                          `CREATED`                                 `STATUS`
		`d5b2e2f9 portainer/portainer-ce:latest "/portainer" 2 weeks ago Up 9 days`
4) Log into your Portainer Server in a web browser at URL `https://[address]:9443`


## Deploy Portainer CE in Docker Swarm on Linux
1) Retrieve the stack YML manifest:
		```curl -L https://downloads.portainer.io/ce2-19/portainer-agent-stack.yml -o portainer-agent-stack.yml```
2) Use the downloaded YML manifest to deploy your stack:
		```docker stack deploy -c portainer-agent-stack.yml portainer```
3) Check to see whether the Portainer Server container has started by running `docker ps`
		*Example response showing active service:*
		`root@server:~# docker ps`		
		`CONTAINER_IMAGE`                                          `CREATED`                                 `STATUS`
		`d5b2e2f9 portainer/portainer-ce:latest "/portainer" 2 weeks ago Up 9 days`
4) Log into your Portainer Server in a web browser at URL `https://[address]:9443`


## Add environments to Portainer
Various protocols can be used for [Portainer node monitoring](https://docs.portainer.io/admin/environments/add/docker) including:
 - Portainer Agent (running as a container on the client)
 - URL/IP address
 - Socket
The method that requires least configuration, and least additional external accessibility, is the Portainer Agent.  
Running a docker command on the client machine will install the Portainer agent -- the appropriate docker command can be obtained in Portainer by:
1) Clicking "Environments" in the left side navigation pane
2) Click the blue button labled "+Add Environment" in the top-right corner
3) Click the appropriate environment (Docker Standalone, Docker Swarm, K8S, etc.)
4) Copy the docker string in the middle of the window and execute on the client
5) Enter a name and IP (ending in :9001) in the fields below and click "Connect"


## Updating Portainer (host)
In this example the container name for Portainer is "Portainer"; change this if necessary for your installation.  On the Portainer host run:
```
docker stop portainer && docker rm portainer && docker pull portainer/portainer-ce:latest && docker run -d -p 8000:8000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```



## Updating Portainer Agent (clients)
```
docker stop portainer_agent && docker rm portainer_agent && docker pull portainer/agent:latest && docker run -d -p 9001:9001 --name=portainer_agent --restart=always -v /v
ar/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest
```
