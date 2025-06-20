# Docker Command Cheatsheet

> ***[Install Docker Desktop on Windows](https://docs.docker.com/desktop/windows/install/)***

<br/>

## Docker Login

**Login to a registry:**

```bash
docker login [OPTIONS] [SERVER]

[OPTIONS]:
-u/--username username
-p/--password password

# Example:

1. docker login localhost:8080 // Login to a registry on your localhost
2. docker login
```

**Logout from a registry:**

```bash
docker logout [SERVER]

# Example:
docker logout localhost:8080 // Logout from a registry on your localhost
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Docker Container Commands

**Create a container:**

```bash
docker container create [OPTIONS] IMAGE [COMMAND] [ARG...]

# Example:
docker container create -t -i sofyspace/hello-world --name hello-world
```

**Rename an existing container:**

```bash
docker container rename CONTAINER NEW_NAME

# Example:
docker container rename mssql sqlserver
```

**Run a command in a new container:**

```bash
docker container run [OPTIONS] IMAGE [COMMAND] [ARG...]

# Example:
docker container run -it --name sqlserver -d sofypace/sqlserver
```

**Delete a container:**

```bash
docker container rm [OPTIONS] CONTAINER [CONTAINER...]

# Example:
docker container rm hello-world
```

**Update the configuration of one or more containers:**

```bash
docker container update [OPTIONS] CONTAINER [CONTAINER...]

# Example:
docker container update --memory "1g" --cpuset-cpu "1" golang // update the golang to use 1g of memory and only use cpu core 1
```

**Start a container:**

```bash
docker container start [OPTIONS] CONTAINER [CONTAINER...]

# Example:
docker container start redis
```

**Stop a running container:**

```bash
docker container stop [OPTIONS] CONTAINER [CONTAINER...]

# Example:
docker container stop redis
docker stop $(docker ps -a -q) // To stop all the containers
```

**Stop a running container and start it up again:**

```bash
docker container restart [OPTIONS] CONTAINER [CONTAINER...]

# Example:
docker container restart redis
```

**Pause processes in a running container:**

```bash
docker container pause CONTAINER [CONTAINER...]

# Example:
docker container pause redis
```

**Unpause processes in a running container:**

```bash
docker container unpause CONTAINER [CONTAINER...]

# Example:
docker container unpause redis
```

**Block a container until others stop (after which it prints their exit codes):**

```bash
docker container wait CONTAINER [CONTAINER...]

# Example:
docker container wait redis
```

**Kill a container by sending a SIGKILL to a running container:**

```bash
docker container kill [OPTIONS] CONTAINER [CONTAINER...]

# Example:
docker container kill redis
```

**Attach local standard input, output, and error streams to a running container:**

```bash
docker container attach [OPTIONS] CONTAINER [CONTAINER...]
```