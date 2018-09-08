# This page - https://bit.ly/2oRUZwp

Status
```
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

