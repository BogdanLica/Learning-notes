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
