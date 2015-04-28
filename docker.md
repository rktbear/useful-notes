# Docker

## Overview

Docker is an application container.

Consider that there are three components of a server: hardware, OS kernel, and OS user space.

A virtual machine (software such as VirtualBox or hardware such as a Hypervisor) allows multiple instances of an OS (both kernel and user space) to run on a single piece of hardware.

An application container allows multiple OS user space instances to run on a single OS kernel.

Docker runs as a user space process on linux **only** that leverages the linux kernel LXC functionality to create and manage application containers.

## Terminology

**Host OS**: The OS user space instance that started the docker process and will start all other docker containers.

**Image**:

**Contanier**: A OS user space instance created based on an image.

## Commands

### Building an Image

- `docker build -t <image_name> <path_to_docker_file>`

### Starting a Container

- `docker run -n <container_name> <image_name>`
- `docker run -n <container_name> <image_name> <command>`

### Run a command in a running Container

- `docker exec -t -i <container_name> <command>`

### Show all running Container

- `docker ps`

### Show logs from a Container

- `docker logs <container_name>`

## Dockerfile

```
FROM ubuntu:14.04
RUN apt-get install -y openssh-server

```
