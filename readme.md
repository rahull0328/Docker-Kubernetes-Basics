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

## Q. What is a Docker Namespace?

A namespace is one of the Linux features and an important concept of containers. Namespace adds a layer of isolation in containers. Docker provides various namespaces in order to stay portable and not affect the underlying host system. Few namespace types supported by Docker – PID, Mount, IPC, User, Network

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the lifecycle of a Docker Container?

Docker containers have the following lifecycle:

1. Create a container
1. Run the container
1. Pause the container(optional)
1. Un-pause the container(optional)
1. Start the container
1. Stop the container
1. Restart the container
1. Kill the container
1. Destroy the container

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is Docker Machine?

Docker machine is a tool that lets you install Docker Engine on virtual hosts. These hosts can now be managed using the docker-machine commands. Docker machine also lets you provision Docker Swarm Clusters.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Suppose you have 3 containers running and out of these, you wish to access one of them. How do you access a running container?

The following command lets us access a running container:

```js
docker exec -it bash
```

The exec command lets you get inside a container and work with it.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Will you lose your data, when a docker container exits?

No, you won\'t lose any data when Docker container exits. Any data that your application writes to the container gets preserved on the disk until you explicitly delete the container. The file system for the container persists even after the container halts.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Where all do you think Docker is being used?

Docker is being used in the following areas:

* **Simplifying configuration**: Docker lets you put your environment and configuration into code and deploy it.
* **Code Pipeline Management**: There are different systems used for development and production. As the code travels from development to testing to production, it goes through a difference in the environment. Docker helps in maintaining the code pipeline consistency.
* **Developer Productivity**: Using Docker for development gives us two things – We\'re closer to production and development environment is built faster.
* **Application Isolation**: As containers are applications wrapped together with all dependencies, your apps are isolated. They can work by themselves on any hardware that supports Docker.
* **Debugging Capabilities**: Docker supports various debugging tools that are not specific to containers but work well with containers.
* **Multi-tenancy**: Docker lets you have multi-tenant applications avoiding redundancy in your codes and deployments.
* **Rapid Deployment**: Docker eliminates the need to boost an entire OS from scratch, reducing the deployment time.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How is Docker different from other containerization methods?

Docker containers are very easy to deploy in any cloud platform. It can get more applications running on the same hardware when compared to other technologies, it makes it easy for developers to quickly create, ready-to-run containerized applications and it makes managing and deploying applications much easier. You can even share containers with your applications.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Can I use JSON instead of YAML for my compose file in Docker?

You can use JSON instead of YAML for your compose file, to use JSON file with compose, specify the JSON filename to use,
for eg:

```js
docker-compose -f docker-compose.json up
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the Difference Between Containers and Virtual Machines?

<p align="center">
  <img src="assets/container-vs-virtual-machine.png" alt="Containers and Virtual Machines" width="600px" />
</p>

**Virtual Machines:**

A virtual machine (VM) is best described as a software program that emulates the functionality of a physical hardware or computing system. It runs on top of an emulating software, called the hypervisor, which replicates the functionality of the underlying physical hardware resources with a software environment. These resources may be referred to as the host machine, while the VM that runs on the hypervisor is often called a guest machine.

The virtual machine contains all necessary elements to run the apps, including:

* Computing
* Storage
* Memory
* Networking
* Hardware functionality available as a virtualized system

The VM may also contain the necessary system binaries and libraries to run the apps. The actual operating system (OS), however, is managed and executed using the hypervisor.

**Containers:**

Containerization creates abstraction at an OS level that allows individual, modular, and distinct functionality of the app to run independently. As a result, several isolated workloads—the containers—can dynamically operate using the same physical resources.

A less technical definition of containers might be: a unit of software that is lightweight but still bundles the code, its dependencies, and the configuration altogether into a single image. Containers can run:

* On top bare metal servers
* On top hypervisors
* In cloud infrastructure

Containers share all necessary capabilities with the VM to operate as an isolated OS environment for a modular app functionality with one key difference. Using a containerization engine, such as the Docker Engine, containers create several isolated OS environments within the same host system kernel, which can be shared with other containers dedicated to run different functions of the app. Only bins, libraries, and other runtime components are developed or executed separately for each container, which makes them more resource efficient as compared to VMs.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is Hypervisor?

A hypervisor is a software that makes virtualization possible. It is also called Virtual Machine Monitor. It divides the host system and allocates the resources to each divided virtual environment. You can basically have multiple OS on a single host system. There are two types of Hypervisors:

* **Type 1:** It\'s also called Native Hypervisor or Bare metal Hypervisor. It runs directly on the underlying host system. It has direct access to your host\'s system hardware and hence does not require a base server operating system.
* **Type 2:** This kind of hypervisor makes use of the underlying host operating system. It\'s also called Hosted Hypervisor.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is virtualization?

Virtualization is the process of creating a software-based, virtual version of something(compute storage, servers, application, etc.). These virtual versions or environments are created from a single physical hardware system. Virtualization lets you split one system into many different sections which act like separate, distinct individual systems. A software called Hypervisor makes this kind of splitting possible. The virtual environment created by the hypervisor is called Virtual Machine.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is containerization?

Usually, in the software development process, code developed on one machine might not work perfectly fine on any other machine because of the dependencies. This problem was solved by the containerization concept. So basically, an application that is being developed and deployed is bundled and wrapped together with all its configuration files and dependencies. This bundle is called a container. Now when you wish to run the application on another system, the container is deployed which will give a bug-free environment as all the dependencies and libraries are wrapped together. Most famous containerization environments are Docker and Kubernetes.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>
