#Hello Docker
There are 2 types of repositories for docker images public => [Docker Hub](https://hub.docker.com/) or private. 

Run a Redis server in interactive mode (`-ti`) and delete on exit (`--rm`).
```sh
$ docker run -ti --rm --name quick-redis redis
```

Now we can easily connect to this server by "linking" the container or connect to any external Redis server instance.

```sh
$ docker run -it --rm --link quick-redis:redis redis redis-cli -h redis -p 6379
redis:6379> PING
```

In this case we`re using Redis from a container where is running a redis client, but what if we want to use redis from our Host? 
