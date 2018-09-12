# This page - https://bit.ly/2MezS0z
## Part-1. Getting started - Docker environment
### Docker CLI
```docker
docker [resource/object] [command] [options] [args]
```
### Display Docker version and info
```docker
1. $ docker --version
2. $ docker version
3. $ docker info
```
### Explore Docker Platform
```
4. $ docker image ls (list images)
5. $ docker container ls (or ps) (list containers)
6. $ docker volume ls
7. $ docker network ls 
```
## Part-2. Create and Run first container

### Pull image (Minimal linux)
```docker
1. $ docker image pull alpine
2. $ docker image ls
3. $ docker image history alpine
```
### Create, start, stop, attach, remove container
```docker
4. $ docker container create -it alpine 
5. $ docker container ps -a
6. $ docker container create -it --name alpine1 alpine
7. $ docker container start alpine1
8. $ docker container attach alpine1
	/# cat /etc/os-release ; exit
9 $ docker container start alpine1; 
10. $ docker container exec alpine1 cat /etc/issue 
11. $ docker container rm alpine1
```
## Part-3.  Detached mode & logs & exec commands 
```
1. $ docker container run -it --name alpine1 --rm alpine
	/# ps aux; exit
2. $ docker container run -d -it --name alpine2 alpine (detached)
3. $ docker container exec alpine2 cat /etc/os-release
4. $ docker container attach alpine2
	/$ exit
``` 
## Part-4. We are big chill (Example)
```
1. $ git clone https://github.com/spkane/wearebigchill.git --config core.autocrlf=input
2. $ cd wearebigchill
3. $ docker image build -t wearebigchill:beta .
4. $ docker image ls
5. $ docker container run --name wearebigchill -p 8080:80 wearebigchill:beta
6. $ docker container rm --force wearebigchill
```
or
```
1. $ docker container run --name wearebigchill -p 8080:80 rselva/wearebigchill:beta
```
## Part-5. Static web application with nginx
```
1. $ mkdir html ; echo "<h2>Welcom to my blog!</h1>" > html\index.html
2. $ docker run --name docker-nginx -p 8080:80 -d -v html:/usr/share/nginx/html nginx
3. $ http://localhost:8080
4. $ docker container exec -it docker-nginx sh
5. $ docker container rm --force docker-nginx
```

## Part-6. Dockerizing an applicatiion - Creating an image, Running a container, Sharing it
### Java Application-> Save as Application.java
```java
import java.time.Instant;
public class Application {

	public static void main(String[] args) {
		System.out.println("Time now is "+ Instant.now());
	}
	
}
```
### Dockerfile  -> Save as Dockerfile
```
FROM openjdk:8-jdk-alpine3.8
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
RUN javac Application.java
CMD ["java", "Application"]
```

### Creating image 
$ docker image build -t {tag} {build context}
```
$ docker image build -t time:beta .
$ docker image ls
```
### Creating Container
```
$ docker container run time:beta
$ docker container run --name time-instance time:beta
```
### Sharing (shipping an image)
#### Create HUBID @ [https://hub.docker.com/](https://hub.docker.com/)
```
$ docker login
$  cat ~/.docker/config.json
```
```json
{
    "auths": {
        "https://index.docker.io/v1/": {
        }
    }
}
```
```
$ docker image tag time:beta ${HUB_USER}/time:beta (rselva/time:beta)
$ docker image push rselva/time:beta 
$ docker image rm rselva/time:beta
$ docker iamge ls
$ docker container run --rm rselva/time:beta
```

## Part-7. Docker in Windows
```
$ docker run -it --cap-add SYS_ADMIN --cap-add SYS_PTRACE --pid=host alpine nsenter -t 1  -m -u -n -i sh
$ cat etc/os-release
$ cat etc/issue
$ exit
```
## Part-8. Saving the container state
```
1. $ docker images
2.  $ docker image tag alpine:latest alpine:beta
3. $ docker container run --name myalpine -it alpine:beta sh
4. $ docker container ps
5. $ docker container ps -a
6. $ docker container start myalpine
7. $ docker container attach myalpine
8. $ docker container commit myalpine alpine:beta2
9. $ docker image history alpine:beta2
```
## Part-9. Store App example 
**Store-App**<br>
	+ product-service<br>
	+ web-app <br> //Not covered today
	
### Step 1. Clone the repo 
```
1. $ git clone https://github.com/rselva/store-app.git
2. $ cd store-app
```
### Step 2. Product service
#### Dockerize and run
```
1. $ cd product-service
####### If maven available #########
Building the image 
2. $ mvn clean package   --> .\target\product-service-0.1.0.jar
3. $ cat Dockerfile
	FROM openjdk:8-jdk-alpine
	VOLUME /tmp
	ARG JAR_FILE
	COPY ${JAR_FILE} app.jar
	ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
4. $ docker image build --build-arg JAR_FILE=target/product-service-0.1.0.jar -t rselva/product-service:beta . 
5. $ docker image push rselva/product-service:beta
#####################################
6. $ docker container run --rm -d -p 8080:8080 --name product-service rselva/product-service:beta
	http://localhost:8080
## Clean up
7. $ docker container rm --force product-service
```

### Part 10. Slack Bot
?
