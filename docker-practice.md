# Docker Workshop

1. [Introduction](#1-introduction)
1. [Images and Containers](#2-images-and-containers)
1. [Create and Start Containers](#3-create-and-start-containers)
1. [Logs, Stop and Kill Containers](#4-logs-stop-and-kill-containers)
1. [Inspect and Remove Containers](#5-inspect-and-remove-containers)
1. [Run a Command in a Running Container with exec](#6-run-a-command-in-a-running-container-with-exec)
1. [Creating Custom Image](#7-creating-custom-image)
1. [Creating an Image from a Dockerfile](#8-creating-an-image-from-a-dockerfile)
1. [COPY and ADD commands](#9-copy-and-add-commands)
1. [Dockerizing a Nodejs project and deploy in Docker-Hub](#10-dockerizing-a-nodejs-project-and-deploy-in-docker-hub)
1. [React and SQL-Server connectivity](#11-react-and-sql-server-connectivity)
1. [Docker Compose](#12-docker-compose)

<br/>

## 1. Introduction

* [Containers and Virtual Machines](https://www.docker.com/resources/what-container)
* [Docker Hub](https://hub.docker.com/)
* Docker Installation
* [VS Code docker plugin](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

```js
docker version          // display docker version 
docker info 
docker run hello-world  // check image in local and download from docker hub 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 2. Images and Containers

```js
docker container ls         // Display list of running containers  
docker ps                   // Display list of running containers  
docker container ls -a      // Display list of container history 
docker image ls             // Display list of images
docker images               // Display list of images 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 3. Create and Start Containers

```js
docker container run hello-world        // more simplified command 
docker container run busybox            // It is tiny versions of many common UNIX utilities into a single small executable 
docker container run busybox ls         // display list of directories 
docker container ls -a                  // display history of containers was running 
docker container run hello-world
docker container create hello-world     // returns id of conatiner created 
docker container ls -a
docker container start -a <container-id> // Start a container using container-id, -a = Attach STDOUT/STDERR and forward signals 
docker conatiner ls -a 
docker system prune --all                // Remove all dangling and unused images 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 4. Logs, Stop, and Kill Containers

```js
docker container ls
docker container create busybox ls 
docker container start <container-id>
docker container logs <container-id>
ping google.com
docker container create busybox ping google.com
docker container ls -a
docker container start <container-id>
docker container ls -a
docker container stop <container-id>     // Does the cleanup before stopping the conatiner 
docker container kill <container-id>     // Stop the container immediately 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 5. Inspect and Remove Containers

```js
docker container ls -a 
docker container inspect <container-id>   // Inspect docker image 
docker container ls -a
docker container rm <container-id>        // Remove container 
docker container rm -f <container-id>     // Force removal container 
docker system prune --all
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 6. Run a Command in a Running Container with exec

```js
docker container run redis                       // Redis is an open-source, networked, in-memory, key-value data store 
new terminal > docker container ls -a
docker container exec <container-id> redis-cli     // Execute "redis-cli" in local terminal 
docker container exec -it <container-id> redis-cli // Execute "redis-cli" command inside redis terminal 
# help
# exit
docker container exec -it <container-id> sh
# cd /
# ls 
# exit
docker container run -it busybox sh       // Open sh terminal in busybox 
# ls -la                                  // Show list of files and directories 
# exit
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>