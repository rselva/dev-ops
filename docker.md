## Docker (access the host OS)
docker run -it --cap-add SYS_ADMIN --cap-add SYS_PTRACE --pid=host debian nsenter -t 1  -m -u -n -i sh (--privilleged)

## Docker and Docker Compose (client-only)  downloads
https://github.com/docker/compose/releases
https://download.docker.com/