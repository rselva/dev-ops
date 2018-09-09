# This page - https://bit.ly/2QhdmY8

## 1. Exploring the docker installation
```
## Docker CLI commands
docker
docker container --help

## Display Docker version and info
docker --version
docker version
docker info

## List Docker images
docker image ls

## Pull docker image
docker pull hello-world

## Execute Docker image
docker run hello-world

## List Docker containers (running, all, all in quiet mode)
docker container ls
docker container ls --all
docker container ls -aq

PS:> docker container ps (list all running containers)
PS:> docker image ls  (list all images in local image cache)
PS:> docker image pull alpine ( pull busybox image from hub.docker.com) [docker.io:5000/busybox:latest]
PS:> docker image ls
PS:> docker container run alpine cat /etc/os-release

```
## 2. Dockerizing an applicatiion - Creating an image, Running a container, Sharing it
### Java Application
```
import java.time.Instant;
public class Applicatopm {

	public static void main(String[] args) {
		System.out.println("Time now is "+ Instant.now());
	}
	
}
```
### Dockerfile 
```
FROM openjdk:8-jdk-alpine3.8
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
RUN javac Applicatopm.java
CMD ["java", "Applicatopm"]
```

### Creating image 
```
$ docker image build -t time:beta .
$ docker image ls
```
### Creating Container
```
$ docker container run time:beta .
$ docker container --name time-instance time:beta
```
## 3. Exploring docker machine VM

```
$ docker run -it --cap-add SYS_ADMIN --cap-add SYS_PTRACE --pid=host debian nsenter -t 1  -m -u -n -i sh
```
```
cat etc/os-release
exit
```
## 4. Handling Containers
```


