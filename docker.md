# Docker Interview Questions

> *Click <img src="assets/star.png" width="18" height="18" align="absmiddle" title="Star" /> if you like the project. Your contributions are heartily ♡ welcome.*

## Table of Contents

* *[Docker Workshop](docker-practice.md)*
* *[Jenkins Interview Questions](jenkins.md)*
* *[Docker Interview Questions](docker.md)*
* *[Kubernetes Interview Questions](kubernetes.md)*
* *[Cloud Computing Interview Questions](cloud.md)*

## Q. ***What is the Difference Between Containers and Virtual Machines?***

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
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Hypervisor?***

A hypervisor is a software that makes virtualization possible. It is also called Virtual Machine Monitor. It divides the host system and allocates the resources to each divided virtual environment. You can basically have multiple OS on a single host system. There are two types of Hypervisors:

* **Type 1:** It\'s also called Native Hypervisor or Bare metal Hypervisor. It runs directly on the underlying host system. It has direct access to your host\'s system hardware and hence does not require a base server operating system.
* **Type 2:** This kind of hypervisor makes use of the underlying host operating system. It\'s also called Hosted Hypervisor.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is virtualization?***

Virtualization is the process of creating a software-based, virtual version of something(compute storage, servers, application, etc.). These virtual versions or environments are created from a single physical hardware system. Virtualization lets you split one system into many different sections which act like separate, distinct individual systems. A software called Hypervisor makes this kind of splitting possible. The virtual environment created by the hypervisor is called Virtual Machine.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is containerization?***

Usually, in the software development process, code developed on one machine might not work perfectly fine on any other machine because of the dependencies. This problem was solved by the containerization concept. So basically, an application that is being developed and deployed is bundled and wrapped together with all its configuration files and dependencies. This bundle is called a container. Now when you wish to run the application on another system, the container is deployed which will give a bug-free environment as all the dependencies and libraries are wrapped together. Most famous containerization environments are Docker and Kubernetes.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Difference between virtualization and containerization***

Containers provide an isolated environment for running the application. The entire user space is explicitly dedicated to the application. Any changes made inside the container is never reflected on the host or even other containers running on the same host. Containers are an abstraction of the application layer. Each container is a different application.

Whereas in Virtualization, hypervisors provide an entire virtual machine to the guest(including Kernal). Virtual machines are an abstraction of the hardware layer. Each VM is a physical machine. VM is more isolated and heavy and takes a lot time to start.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Docker?***

Docker is a containerization platform which packages your application and all its dependencies together in the form of containers so as to ensure that your application works seamlessly in any environment, be it development, test or production.
Docker containers, wrap a piece of software in a complete filesystem that contains everything needed to run: code, runtime, system tools, system libraries, etc.
It wraps basically anything that can be installed on a server. This guarantees that the software will always run the same, regardless of its environment.

<p align="center">
  <img src="assets/docker-architecture.png" alt="Docker Architecture" width="600px" />
</p>

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a Docker Container?***

Docker containers include the application and all of its dependencies. It shares the kernel with other containers, running as isolated processes in user space on the host operating system. Docker containers are not tied to any specific infrastructure: they run on any computer, on any infrastructure, and in any cloud. Docker containers are basically runtime instances of Docker images.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are Docker Images?***

Docker image is the source of Docker container. In other words, Docker images are used to create containers. When a user runs a Docker image, an instance of a container is created. These docker images can be deployed to any Docker environment.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Docker Hub?***

Docker images create docker containers. There has to be a registry where these docker images live. This registry is Docker Hub. Users can pick up images from Docker Hub and use them to create customized images and containers. Currently, the Docker Hub is the world\'s largest public repository of image containers.

**Reference:**

* **[https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain Docker Architecture?***

The Docker works on client-server architecture. The Docker client establishes communication with the Docker Daemon. The Docker client and Daemon can run on the same system. A Docket client can also be connected to a remote Docker Daemon. The different types of Docker components in a Docker architecture are–

* **Docker Client**: This performs Docker build pull and run operations to establish communication with the Docker Host. The Docker command uses Docker API to call the queries to be run.
* **Docker Host**: This component contains Docker Daemon, Containers and its images. The images will be the kind of metadata for the applications which are containerized in the containers. The Docker Daemon establishes a connection with Registry.
* **Registry**: This component will be storing the Docker images. The public registries are Docker Hub and Docker Cloud which can be s used by anyone.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a Dockerfile?***

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
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Tell us something about Docker Compose.***

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
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How is Dockerfile different from Docker Compose***

A Dockerfile is a simple text file that contains the commands a user could call to assemble an image whereas Docker Compose is a tool for defining and running multi-container Docker applications. Docker Compose define the services that make up your app in docker-compose.yml so they can be run together in an isolated environment. It get an app running in one command by just running docker-compose up. Docker compose uses the Dockerfile if one add the build command to your project's docker-compose.yml. Your Docker workflow should be to build a suitable Dockerfile for each image you wish to create, then use compose to assemble the images using the build command.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Docker Swarm?***

Docker Swarm is native clustering for Docker. It turns a pool of Docker hosts into a single, virtual Docker host. Docker Swarm serves the standard Docker API, any tool that already communicates with a Docker daemon can use Swarm to transparently scale to multiple hosts.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a Docker Namespace?***

A namespace is one of the Linux features and an important concept of containers. Namespace adds a layer of isolation in containers. Docker provides various namespaces in order to stay portable and not affect the underlying host system. Few namespace types supported by Docker – PID, Mount, IPC, User, Network

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the lifecycle of a Docker Container?***

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
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Docker Machine?***

Docker machine is a tool that lets you install Docker Engine on virtual hosts. These hosts can now be managed using the docker-machine commands. Docker machine also lets you provision Docker Swarm Clusters.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Suppose you have 3 containers running and out of these, you wish to access one of them. How do you access a running container?***

The following command lets us access a running container:

```js
docker exec -it bash
```

The exec command lets you get inside a container and work with it.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Will you lose your data, when a docker container exits?***

No, you won\'t lose any data when Docker container exits. Any data that your application writes to the container gets preserved on the disk until you explicitly delete the container. The file system for the container persists even after the container halts.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Where all do you think Docker is being used?***

Docker is being used in the following areas:

* **Simplifying configuration**: Docker lets you put your environment and configuration into code and deploy it.
* **Code Pipeline Management**: There are different systems used for development and production. As the code travels from development to testing to production, it goes through a difference in the environment. Docker helps in maintaining the code pipeline consistency.
* **Developer Productivity**: Using Docker for development gives us two things – We\'re closer to production and development environment is built faster.
* **Application Isolation**: As containers are applications wrapped together with all dependencies, your apps are isolated. They can work by themselves on any hardware that supports Docker.
* **Debugging Capabilities**: Docker supports various debugging tools that are not specific to containers but work well with containers.
* **Multi-tenancy**: Docker lets you have multi-tenant applications avoiding redundancy in your codes and deployments.
* **Rapid Deployment**: Docker eliminates the need to boost an entire OS from scratch, reducing the deployment time.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How is Docker different from other containerization methods?***

Docker containers are very easy to deploy in any cloud platform. It can get more applications running on the same hardware when compared to other technologies, it makes it easy for developers to quickly create, ready-to-run containerized applications and it makes managing and deploying applications much easier. You can even share containers with your applications.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can I use JSON instead of YAML for my compose file in Docker?***

You can use JSON instead of YAML for your compose file, to use JSON file with compose, specify the JSON filename to use,
for eg:

```js
docker-compose -f docker-compose.json up
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How have you used Docker in your previous position?***

Explain how you have used Docker to help rapid deployment. Explain how you have scripted Docker and used it with other tools like Puppet, Chef or Jenkins. If you have no past practical experience in Docker and instead have experience with other tools in a similar space, be honest and explain the same. In this case, it makes sense if you can compare other tools to Docker in terms of functionality.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How far do Docker containers scale? Are there any requirements for the same?***

Large web deployments like Google and Twitter and platform providers such as Heroku and dotCloud, all run on container technology. Containers can be scaled to hundreds of thousands or even millions of them running in parallel. Talking about requirements, containers require the memory and the OS at all the times and a way to use this memory efficiently when scaled.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Is there a way to identify the status of a Docker container?***

There are six possible states a container can be at any given point –

1. Created
1. Running
1. Paused
1. Restarting
1. Exited
1. Dead.

Use the following command to check for docker state at any given point: `$ docker ps` The above command lists down only running containers by default. To look for all containers, use the following command: `$ docker ps -a`

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can you remove a paused container from Docker?***

The answer is no. You cannot remove a paused container. The container has to be in the stopped state before it can be removed.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can a container restart by itself?***

No, it\'s not possible for a container to restart by itself. By default the flag -restart is set to false.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Is it better to directly remove the container using the rm command or stop the container followed by remove container?***

Its always better to stop the container and then remove it using the remove command. `$ docker stop <coontainer_id> $ docker rm -f <container_id>`
Stopping the container and then removing it will allow sending SIG_HUP signal to recipients. This will ensure that all the containers have enough time to clean up their tasks. This method is considered a good practice, avoiding unwanted errors.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Will cloud overtake the use of Containerization?***

Docker containers are gaining popularity but at the same time, Cloud services are giving a good fight. In my personal opinion, Docker will never be replaced by Cloud. Using cloud services with containerization will definitely hype the game. Organizations need to take their requirements and dependencies into consideration into the picture and decide what\'s best for them. Most of the companies have integrated Docker with the cloud. This way they can make the best out of both the technologies.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How many containers can run per host?***

There can be as many containers as you wish per host. Docker does not put any restrictions on it. But you need to consider every container needs storage space, CPU and memory which the hardware needs to support. You also need to consider the application size. Containers are considered to be lightweight but very dependant on the host OS.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Is it a good practice to run stateful applications on Docker? or What type of applications - Stateless or Stateful are more suitable for Docker Container?***

The concept behind stateful applications is that they store their data onto the local file system. You need to decide to move the application to another machine, retrieving data becomes painful. I honestly would not prefer running stateful applications on Docker.

Suppose you have an application that has many dependant services. Will docker compose wait for the current container to be ready to move to the running of the next service?
The answer is yes. Docker compose always runs in the dependency order. These dependencies are specifications like depends_on, links, volumes_from, etc.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How will you monitor Docker in production?***

Docker provides functionalities like docker stats and docker events to monitor docker in production. Docker stats provides CPU and memory usage of the container. Docker events provide information about the activities taking place in the docker daemon.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Is it a good practice to run Docker compose in production?***

Yes, using docker compose in production is the best practical application of docker compose. When you define applications with compose, you can use this compose definition in various production stages like CI, staging, testing, etc.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What changes are expected in your docker compose file while moving it to production?***

These are the following changes you need make to your compose file before migrating your application to the production environment:

* Remove volume bindings, so the code stays inside the container and cannot be changed from outside the container.
* Binding to different ports on the host.
* Specify a restart policy
* Add extra services like log aggregator

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Are you aware of load balancing across containers and hosts? How does it work?***

While using docker service with multiple containers across different hosts, you come across the need to load balance the incoming traffic. Load balancing and HAProxy is basically used to balance the incoming traffic across different available(healthy) containers. If one container crashes, another container should automatically start running and the traffic should be re-routed to this new running container. Load balancing and HAProxy works around this concept.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a Docker Registry?***

A Docker Registry is a place where all the Docker Images will be stored and Docker Cloud and Docker Hub are the public registries where these images can be hosted upon. The Docker hub is the default storage for the Docker Images. An own registry can also be set up as per the requirement. Docker Data Center (DDC) can also be used which includes DTR (Docker Trusted Registry). Docker store will provide the feature of buying and selling the Docker images.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is DockerHub?***

DockerHub is a cloud-based registry service which allows you to link to code repositories, build your images and test them, stores manually pushed images, and links to Docker cloud so you can deploy images to your hosts. It provides a centralized resource for container image discovery, distribution and change management, user and team collaboration, and workflow automation throughout the development pipeline.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to create Docker container***

We can use Docker image to create Docker container by using the below command:

```js
docker run -t -i command name
```

This command will create and start a container.If you want to verify the list of all running container with the status on a host use the below command:

```js
docker ps -a
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Does Docker container package up the entire OS?***

Docker containers do not package up the OS. They package up the applications with everything that the application needs to run. The engine is installed on top of the OS running on a host. Containers share the OS kernel allowing a single host to run multiple containers.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Describe how many ways are available to configure Docker daemon?***

There are two ways to configure the Docker daemon:

* Using a JSON configuration file. This is the preferred option, since it keeps all configurations in a single place.
* Using flags when starting dockerd. You can use both of these options together as long as you don’t specify the same option both as a flag and in the JSON file. If that happens, the Docker daemon won’t start and prints an error message.

```js
$ dockerd --debug --tls=true --tlscert=/var/docker/server.pem --tlskey=/var/docker/serverkey.pem
--host tcp://<Host_IP>:2376
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can you list reasons why Container Networking is so important?***

* Containers need to talk to external world.
* Reach Containers from external world to use the service that Containers provides.
* Allows Containers to talk to host machine.
* Inter-container connectivity in same host and across hosts.
* Discover services provided by containers automatically.
* Load balance traffic between different containers in a service.
* Provide secure multi-tenant services.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to create a user-defined Bridge network ?***

To create a user-defined bridge network, one can use the docker network create command -

`$ docker network create mynet`

You can specify the subnet, the IP address range, the gateway, and other options. See the docker network create reference or the output of docker network create --help for details.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is memory-swap flag?***

`--memory-swap` is a modifier flag that only has meaning if `--memory` is also set. Using swap allows the container to write excess memory requirements to disk when the container has exhausted all the RAM that is available to it. There is a performance penalty for applications that swap memory to disk often.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can you explain different volume mount types available in Docker?***

There are three mount types available in Docker · Volumes are stored in a part of the host filesystem which is managed by Docker (`/var/lib/docker/volumes/` on Linux). Non-Docker processes should not modify this part of the filesystem. Volumes are the best way to persist data in Docker. · Bind mounts may be stored anywhere on the host system. They may even be important system files or directories. Non-Docker processes on the Docker host or a Docker container can modify them at any time. · tmpfs mounts are stored in the host system’s memory only, and are never written to the host system’s filesystem.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to share data among DockerHost?***

Ways to achieve this when developing your applications. One is to add logic to your application to store files on a cloud object storage system like Amazon S3. Another is to create volumes with a driver that supports writing files to an external storage system like NFS or Amazon S3. Volume drivers allow you to abstract the underlying storage system from the application logic. For example, if your services use a volume with an NFS driver, you can update the services to use a different driver, as an example to store data in the cloud, without changing the application logic.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to Backup, Restore, or Migrate data volumes under Docker container?***

Steps to Backup a container

1. Launch a new container and mount the volume from the dbstore container
1. Mount a local host directory as /backup
1. Pass a command that tars the contents of the dbdata volume to a backup.tar file inside our /backup directory.

`$ docker run --rm --volumes-from dbstore -v $(pwd):/backup ubuntu tar cvf /backup/backup.tar /dbdata` Restore container from backup With the backup just created, you can restore it to the same container, or another that you made elsewhere. For example, create a new container named dbstore2: `$ docker run -v /dbdata --name dbstore2 ubuntu /bin/bash`

Then un-tar the backup file in the new container`s data volume:

```js
docker run --rm --volumes-from dbstore2 -v $(pwd):/backup ubuntu bash -c "cd /dbdata && tar xvf /backup/backup.tar --strip 1"
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to Configure Automated Builds on DockerHub***

You can build your images automatically from a build context stored in a repository. A build context is a Dockerfile and any files at a specific location. For an automated build, the build context is a repository containing a Dockerfile.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>