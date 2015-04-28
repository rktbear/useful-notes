# Docker

## Overview

Docker is an application container.

Consider that there are three components of a server: hardware, OS kernel, and OS user space.

A virtual machine (software such as VirtualBox or hardware such as a Hypervisor) allows multiple instances of an OS (both kernel and user space) to run on a single piece of hardware.

An application container allows multiple OS user space instances to run on a single OS kernel. Filesystem and users/groups are segmented.

Docker runs as a user space process on linux only that leverages the linux kernel LXC functionality to create and manage application containers.

## Terminology

**Host OS**: The OS user space instance that started the docker process and will start all other docker containers.

**Image**: All files that make up a container.

**Contanier**: A OS user space instance created based on an image.

## Cheat Sheet

### Building an image

- `docker build -t <image_name> <path_to_docker_file>`

### Starting a container

When a container starts it executes it will execute a command and then terminate.

Start a container without any commands (depends on `CMD` in Dockerfile):
- `docker run -n <container_name> <image_name>`

Start a container and execute a command:
- `docker run -n <container_name> <image_name> <command>`

Start a container and run `bash`:
- `docker run -n <container_name> <image_name> bash`

Start a container and run `echo "hello world!":
- `docker run -n <container_name> <image_name> echo "hello world!"`

### Run a command in a running container

- `docker exec -t -i <container_name> <command>`

### Show all running containers

- `docker ps`

### Show logs from a container

- `docker logs <container_name>`

## Dockerfile

A series of operations that are executed when building the image. `CMD` is only executed when the container starts.

Reference of all Dockerfile commands [https://docs.docker.com/reference/builder/](https://docs.docker.com/reference/builder/).

### Java Server

A stand-alone Java server that runs on port 8081.

The application is a jar file that is packaged up in `app.tar.gz` and will be extracted into `/opt/app` by the `ADD` command.  

```
FROM dockerfile/java:oracle-java7

RUN rm -rf /opt/app
RUN mkdir -p /opt/app
ADD app.tar.gz /opt/app
EXPOSE 8081
CMD cd /usr/bin/java && /opt/app/app.jar
```
