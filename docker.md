
# Remote access 
## Server

Config file

    /etc/docker/daemon.json
    {
        "hosts":["unix:///var/run/docker.sock","tcp://127.0.0.1:2375"]
    }

Procedure 

    $ sudo docker restart
    $ sudo netstat -lntp | grep dockerd 

## Client
**Downloads** <br>
https://github.com/docker/compose/releases - Docker compose <br>
https://download.docker.com/ -Docker <br>

**Procedure**

    Linux
    $export DOCKER_HOST=w.x.y.z:2375
    $env | grep DOCKER_HOST
    
    PowerShell
    PS:> Set-Item Env:DOCKER_HOST= "w.x.y.z:2375"
    
    $docker version


# Docker Misc
### Access Docker machine 
    $ docker run -it --cap-add SYS_ADMIN --cap-add SYS_PTRACE --pid=host debian nsenter -t 1  -m -u -n -i sh (--privilleged)
    $ sudo usermod -aG docker {username}

docker rm -vf $(docker ps -aq)
docker rmi -f $(docker images -aq)
docker volume prune -f

docker system prune -a -f
#!/bin/bash

##### remove exited containers:
docker ps --filter status=dead --filter status=exited -aq | xargs -r docker rm -v
    
##### remove unused images:
docker images --no-trunc | grep '<none>' | awk '{ print $3 }' | xargs -r docker rmi

##### remove unused volumes:
find '/var/lib/docker/volumes/' -mindepth 1 -maxdepth 1 -type d | grep -vFf <(
  docker ps -aq | xargs docker inspect | jq -r '.[] | .Mounts | .[] | .Name | select(.)'
) | xargs -r rm -fr

docker volume ls -qf dangling=true | xargs -r docker volume rm

https://lebkowski.name/docker-volumes/

#####
$docker --rm --user <br>
base image from specific version <br>
$layers and size compine commands <br>
jib maven plugin

