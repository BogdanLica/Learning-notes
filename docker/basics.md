# Docker

### What problem does it solve?
* it gives identical environments for testing the code and then for production
* i.e : package an application with all its dependencies into a standardized unit

## *Internals of Docker*
--> docker uses the Linux namespaces to provide the separation between the programs

---
### Namespaces
* mount
  * isolates file access to a given directory
* pid
  * limits what processes can be seen
* net
  * each network interface is present in exactly **one** namespace and can be moved between namespaces
* ipc(interprocess communication)
  * no pipes and no shared memory
* Unix time-sharing system
  * isolate host and domain names
* user
  * separate user IDs for processes
  * i.e: being root in the container, does not mean root on the host

---
### Useful terminal commands

* list running containers
```
docker ps
docker container ls
```
* list all the containers(a container is a running instance of an image)

```
docker ps -a
```
* stop a container
```
docker container stop long_hash
```
* list all the docker images

```
docker images
docker image ls
```
* execute docker image
```
docker run image-name
```

* show more info about the docker instalation
```
docker info
```


---
## Docker Swarm
* a clustering and scheduling tool for clusters of Docker containers
* the **swarm manager** is responsible for validating,logging the state of and distributing instructions to the Docker Swarm Workers
---
## Basics
* an **image** is an executable package that contains every dependency needed to run the application
* a **container** is a running instance of an **image**


## Share an image

#### A *registry* is a collection of repositories, where images are uploaded
* tags are used to give Docker images a version

###### Tag an image
```
docker tag image_name username/repository:tag
```
###### Publish an image
```
docker push username/repository:tag
```



## Cheatsheet

``` bash
## List Docker CLI commands
docker
docker container --help

## Display Docker version and info
docker --version
docker version
docker info

## Execute Docker image
docker run hello-world

## List Docker images
docker image ls

## List Docker containers (running, all, all in quiet mode)
docker container ls
docker container ls --all
docker container ls -aq


docker build -t friendlyhello .  # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyhello  # Run "friendlyname" mapping port 4000 to 80
docker run -d -p 4000:80 friendlyhello         # Same thing, but in detached mode
docker container ls                                # List all running containers
docker container ls -a             # List all containers, even those not running
docker container stop <hash>           # Gracefully stop the specified container
docker container kill <hash>         # Force shutdown of the specified container
docker container rm <hash>        # Remove specified container from this machine
docker container rm $(docker container ls -a -q)         # Remove all containers
docker image ls -a                             # List all images on this machine
docker image rm <image id>            # Remove specified image from this machine
docker image rm $(docker image ls -a -q)   # Remove all images from this machine
docker login             # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag  # Tag <image> for upload to registry
docker push username/repository:tag            # Upload tagged image to registry
docker run username/repository:tag                   # Run image from a registry


docker stack ls                                            # List stacks or apps
docker stack deploy -c <composefile> <appname>  # Run the specified Compose file
docker service ls                 # List running services associated with an app
docker service ps <service>                  # List tasks associated with an app
docker inspect <task or container>                   # Inspect task or container
docker container ls -q                                      # List container IDs
docker stack rm <appname>                             # Tear down an application
docker swarm leave --force      # Take down a single node swarm from the manager

```
---
##### A distributed application can be divided in multiple services
eg
* a service for storing application data in a database
* a service for the front end etc

###### A service only runs one image,but it knows the ports that are goint to be used, how many replicas of the container should be used for the service to be functional.
###### Scaling a service means just changing the number of container instances running by assigning more computing resources
###### This can be done using a **docker-compose.yml** file



---
## Getting Started with Docker
### A docker container has it's own **process space and network interface**
* it has it's own */sbin/init*
* Docker is carrying out client-server work on the UNIX socket( /var/run/docker.sock )
* it has the port 2375 registered, but it is closed by default
#### Containerization technologies
* **LXC (Linux Containers)**
* **OpenVZ**
* **FreeBSD jail**
* **Solaris Containers**

##### The Docker registry is a repository

###### Download an image from the Docker registry
> docker pull name_image

