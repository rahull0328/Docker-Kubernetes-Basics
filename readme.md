# Docker and Kubernetes Basics

> *Click &#9733; if you like the project. Your contributions are heartily ♡ welcome.*

<br/>

## Table of Contents

* *[Docker Workshop](docker-practice.md)*
* *[Docker Command Cheatsheet](docker-commands.md)*
* *[Kubernetes Basics](kubernetes.md)*
* *[Kubernetes Workshop](kubernetes-workshop.md)*
* *[Kubectl Command Cheatsheet](kubernetes-commands.md)*
* *[Cloud Computing Basics](cloud.md)*
* *[Jenkins Interview Questions](jenkins.md)*

<br/>

## Q. What is Docker?

Docker is a containerization platform which packages your application and all its dependencies together in the form of containers so as to ensure that your application works seamlessly in any environment, be it development, test or production.

<p align="center">
  <img src="assets/docker-architecture.png" alt="Docker Architecture" width="600px" />
</p>

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is a Docker Container?

Docker containers include the application and all of its dependencies. It shares the kernel with other containers, running as isolated processes in user space on the host operating system. Docker containers are not tied to any specific infrastructure: they run on any computer, on any infrastructure, and in any cloud. Docker containers are basically runtime instances of Docker images.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What are Docker Images?

Docker image is the source of Docker container. In other words, Docker images are used to create containers. When a user runs a Docker image, an instance of a container is created. These docker images can be deployed to any Docker environment.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is Docker Hub?

Docker images create docker containers. There has to be a registry where these docker images live. This registry is Docker Hub. Users can pick up images from Docker Hub and use them to create customized images and containers. Currently, the Docker Hub is the world\'s largest public repository of image containers.

**Reference:**

* **[https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)**

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Explain Docker Architecture?

The Docker works on client-server architecture. The Docker client establishes communication with the Docker Daemon. The Docker client and Daemon can run on the same system. A Docket client can also be connected to a remote Docker Daemon. The different types of Docker components in a Docker architecture are–

* **Docker Client**: This performs Docker build pull and run operations to establish communication with the Docker Host. The Docker command uses Docker API to call the queries to be run.
* **Docker Host**: This component contains Docker Daemon, Containers and its images. The images will be the kind of metadata for the applications which are containerized in the containers. The Docker Daemon establishes a connection with Registry.
* **Registry**: This component will be storing the Docker images. The public registries are Docker Hub and Docker Cloud which can be s used by anyone.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is a Dockerfile?

Docker can build images automatically by reading the instructions from a file called Dockerfile.
A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.
Using docker build, users can create an automated build that executes several command-line instructions in succession.

**Example:**

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
docker run -p 3000:3000 sofyspace/scm-website         // Project will run on local and will map to docker conatiner port 
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Tell us something about Docker Compose.

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application\'s services. Then, with a single command, you create and start all the services from your configuration.
You can use Docker Compose to create separate containers, host them and get them to communicate with each other. Each container will expose a port for communicating with other containers.

**Example:** Define the MySQL service

```yml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

```js
docker-compose up  // Start the App
docker-compose down   // Removing Volumes
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How is Dockerfile different from Docker Compose

A Dockerfile is a simple text file that contains the commands a user could call to assemble an image whereas Docker Compose is a tool for defining and running multi-container Docker applications. Docker Compose define the services that make up your app in docker-compose.yml so they can be run together in an isolated environment. It get an app running in one command by just running docker-compose up. Docker compose uses the Dockerfile if one add the build command to your project's docker-compose.yml. Your Docker workflow should be to build a suitable Dockerfile for each image you wish to create, then use compose to assemble the images using the build command.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is Docker Swarm?

Docker Swarm is native clustering for Docker. It turns a pool of Docker hosts into a single, virtual Docker host. Docker Swarm serves the standard Docker API, any tool that already communicates with a Docker daemon can use Swarm to transparently scale to multiple hosts.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>