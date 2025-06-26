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

## 7. Creating Custom Image

```js
docker container run -it --name scm-container alpine:latest /bin/sh   // Create a new custom conatiner "scm-container" 
# apk add --update redis                                              // Updates apk package in redis 
# exit                                             
docker container commit scm-container scm-image                       // Creates a new image from "scm-container" 
docker image ls                                                       // display image list 
docker container run scm-image redis-server                           // Star custom container using redis server 
docker container exec -it <container-id> redis-cli                      // Validate redis server using redis-cli 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 8. Creating an Image from a Dockerfile

* **Dockerfile**

```js
FROM alpine:latest
RUN apk add --update redis
CMD ["redis-server"]
```

```js
docker build .                    // Build image from current directory using Dockerfile 
docker image ls                   // View build image 
docker image rm -f <image-id>   // Remove build image 
docker image ls
docker build -t sofyspace/scm-redis:latest .  // Build image from current directory using Dockerfile 
docker run sofyspace/scm-redis
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 9. COPY and ADD Commands

* **Dockerfile**

```js
# From alpine library
FROM alpine

# Copy all the files from source directory to Docker image
COPY ./html_files /app/html

# Copy Text file to Docker image
COPY sample.txt /app/sample.txt

# Copy tar file to Docker image
ADD file.tar /app

# Copy svg file directly from url to Docker image
ADD https://cdnjs.cloudflare.com/ajax/libs/line-awesome/1.3.0/svg/docker.svg /app/images/logo.svg
```

```js
docker build .                  // Build image from current directory using Dockerfile ]
docker image ls   
docker run -it <image-id> sh  // Rnu the build container in interactive mode 
# ls -la                        // Display all directories 
# cd app/                       // app directory 
# ls -la                        // List all files and directories 
# cd ..                         // Parent directory 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## 10. Dockerizing a Nodejs project and deploy in Docker-Hub

```js
npm init  // create package.json file
```

* **index.js**

```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
    res.send('Node.js Server Running!');
});

app.listen(3000, () => {
   console.log(`Node APP Listening at http://localhost:3000/`);
});
```

* **package.json**

```js
{
    "dependencies": {
        "express": "*"
    },
    "scripts": {
        "start": "node index.js"
    }
}
```

* **Dockerfile**

```js
# alpine will download only basic version of node.js
FROM node:alpine

# Instead of root directory, program will use "/usr/app" directory
WORKDIR /usr/app

# Copy local directory to nodejs directory
COPY ./ ./

# Perform npm install
RUN npm install

# Run npm start in command prompt
CMD ["npm", "start"]
```

```js
docker build -t sofyspace/scm-website:latest .        // --tag , -t   ==> Name and optionally a tag in the 'name:tag' format
docker run sofyspace/scm-website                      // Project will run on docker conatiner
docker run -p 3000:3000 sofyspace/scm-website         // Project will run on local and will map to docker conatiner port 
docker login
docker push sofyspace/scm-website                     // Deploy in Docker Hub
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>