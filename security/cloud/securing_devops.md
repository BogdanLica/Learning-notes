## *Continuous Integration*
* quickly integrating new features into the software
* defines a workflow to implement,test and merge features into the product

## *Continuous Delivery*
* automation of deploying software into services available to the customer
* program the infrastructure to manage change rapidly

## *Infrastructure as a Service*
* is the cloud
* the systems are entirely operated by a third party, controllable through API and code

## *Continuous Security*
#### Test Driven Security
* eg: simple controls such as the standard configuration of a Linux server or the security headers that are implemented by a web app
* SSH root login must be disable on all systems
* Systems and applications must be patched within 30 days of its release
* Web applications must use HTTPS and not HTTP
* Secrets and credentials must not be stored in the code itself, but rather in a vault avaiable only to the operator
* Administrative interfaces must be only accessible through VPNs
#### Monitoring and responding to attacks
* eg: fraud and intrusion detection, digital forensics, incident response etc
* when puting a popular service online, at some point, a scanner will pick it and try to break in
#### Assesing risks and maturing security
* looking beyond the technology at the security of the organisation internally and externally

---

## Building a barebone DevOps pipeline
* several components need to be integrated such as
  * a source code repository: BitBucket, GitHub, GitLab
  * a CI platform: Travis CI, Circle CI, Jenkins
  * a container repository: Docker
  * an IaaS provider: GCP, AWS, OpenStack
* basic overview of how it works: **GitHub** hosts the code and calls **CircleCI** when patches are created. **CircleCI** builds the application into a container and pushes it to **Docker Hub**. **AWS** retrieves the new container from **Docker Hub** to upgrade the production environment to the latest version


### Three tier architecture (AWS)
* common pattern in web applications
  * first tier: handles incoming HTTP traffic from the client (catching and load balancing)
  * second tier: processes requests and builds responses
  * third tier: database/other backends that store data for the application
* eg: Client -> Elastic Load Balancing -> Elastic Compute Cloud -> Relational Database Service







---

## Interesting fragments
* "... that **security is highly dependent on the infrastructure flexibility**: if the systems can move fast, issues can be fixed faster and security is better"
* " security must be at the service of the business"