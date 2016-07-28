#Hello Docker
There are 2 types of repositories for docker images public or private; [Docker Hub](https://hub.docker.com/) is the default public repository for Docker.

Run a Redis server in interactive mode (`-ti`) and delete on exit (`--rm`).
```sh
$ docker run -ti --rm --name quick-redis redis
```

Now we can easily connect to this server by "linking" the container or connect to any external Redis server instance.

```sh
$ docker run -it --rm --link quick-redis:redis redis redis-cli -h redis -p 6379
redis:6379> PING
```

In this case we`re using Redis client inside a container to connect to a Redis server that is running in another container,that`s why we need to use --link <container-name>:<network-container-alias> parameter to create a docker network between both cotainers. What if we want to use redis from our main Host?
