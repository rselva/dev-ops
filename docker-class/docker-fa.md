# This page - https://bit.ly/2QhdmY8

Status
```
## List Docker CLI commands
docker
docker container --help

## Display Docker version and info
docker --version
docker version
docker info

## Execute Docker image
docker run hello-world

## List Docker images
docker image ls

## List Docker containers (running, all, all in quiet mode)
docker container ls
docker container ls --all
docker container ls -aq
PS:> docker version
PS:> docker info
PS:> docker run hello-world
```
## Container basics
```
PS:> docker container ps (list all running containers)
PS:> docker image ls  (list all images in local image cache)
PS:> docker image pull busybox ( pull busybox image from hub.docker.com) [docker.io:5000/busybox:latest]
PS:> docker image ls
PS:> docker container run busybox cat /etc/os-release

