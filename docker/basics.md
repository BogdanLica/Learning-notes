# Docker

### What problem does it solve?
* it gives identical environments for testing the code and then for production

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
```
* list all the containers(a container is a running instance of an image)

```
docker ps -a
```
* list all the docker images

```
docker images
```



---
## Docker Swarm
* a clustering and scheduling tool for clusters of Docker containers
* the **swarm manager** is responsible for validating,logging the state of and distributing instructions to the Docker Swarm Workers
