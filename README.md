# Docker Common Commands

## Docker Installation
If you have Windows 10 or OS X and your machine`s hypervisor is activated, you can use a the native version of docker, otherwise you must use Docker Toolbox which has a Virtual Machine with a linux distribution where docker is already installed  

obtaining a list of currently running containers
```sh
$ docker ps
```

### Obtaining a list of all containers running / stopped
```sh
$ docker ps -a
```

### Stopping a container
```sh
$ docker stop <container name>
```

### Removing a container (has to be stopped)
```sh
$ docker rm <container name>
```

### Removing all containers with exited status
```sh
$ docker rm -v $(docker ps -a -q -f status=exited)
```

### Inspecting a container
```sh
$ docker inspect <container name>
```

### Listing docker images locally available
```sh
$ docker images
```

### Pulling an image from docker hub
```sh
$ docker pull nginx
```

### Removing docker images
```sh
$ docker rmi <image name>
```











