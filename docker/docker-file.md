# Dockerfile


## What is a Dockerfile?

Docker builds images automatically by reading the instructions from a Dockerfile which is a text file that contains all commands, in order, needed to build a given image. A Dockerfile adheres to a specific format and set of instructions which you can find at [Dockerfile reference](https://docs.docker.com/engine/reference/builder/).

A Docker image consists of read-only layers each of which represents a Dockerfile instruction. The layers are stacked and each one is a delta of the changes from the previous layer.

```Go
# syntax=docker/dockerfile:1

FROM ubuntu:22.04
COPY . /app
RUN make /app
CMD python /app/app.py
```

In the example above, each instruction creates one layer:

* FROM creates a layer from the ubuntu:22.04 Docker image.
* COPY adds files from your Docker client's current directory.
* RUN builds your application with make.
* CMD specifies what command to run within the container.


# BuildKits 

BuildKit supports loading frontends dynamically from container images. To use an external Dockerfile frontend, the first line of your Dockerfile needs to set the syntax directive pointing to the specific image you want to use:

```
# syntax=docker/dockerfile:1
```

# New feature in 1.4 Here-Documents

```GO
RUN <<EOF
apt-get update
apt-get upgrade -y
apt-get install -y ...
EOF
```

## Example running a multi-line script (Python)

```GO
# syntax=docker/dockerfile:1
FROM debian
RUN <<EOT bash
  set -ex
  apt-get update
  apt-get install -y vim
EOT
```

## Multi-Stage Dockerfile Example (SpringBoot)

```GO
# syntax=docker/dockerfile:1
#Start with a base image containing Maven & Java runtime
FROM maven:3.9.6-eclipse-temurin-21-alpine7 AS build

#Information about who maintains the image
MAINTAINER John Doe

ENV HOME=/home/app
COPY src /home/app/src
COPY pom.xml $HOME
RUN mkdir -p /root/.m2 \
    && mkdir /root/.m2/repository

# Subsequent runs will use local dependencies and execute much faster. (https://www.baeldung.com/ops/docker-cache-maven-dependencies)
RUN --mount=type=cache,target=/root/.m2 mvn -f $HOME/pom.xml clean package -DskipTests

#
# Package stage
#
FROM clipse-temurin:21.0.2_13-jre-alpine
VOLUME /tmp
RUN groupadd -r -g 2000 mygroup && useradd -m -d /home/myuser -u 2000 -r -g mygroup myuser

# Add the application's jar to the container
COPY --from=build ${HOME}/target/demo-0.0.1-SNAPSHOT.jar /usr/local/lib/demo.jar
USER myuser
EXPOSE 8080

#execute the application
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/usr/local/lib/demo.jar"]
```
