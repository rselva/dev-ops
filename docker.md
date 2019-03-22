
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


