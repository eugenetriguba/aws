* Containers that AWS manages (is to containers what EC2 is to virtual machines)
* Uses clusters that runs in different modes
  * EC2 Mode
    * Uses EC2 instances as container hosts
  * Fargate Mode
    * Serverless way of running docker containers

Container Definition

* Tells ECS where the container image is and which port the container uses.
* ECS needs a container definition

Task Definition

* Defines a self-contained application.
* It could have one container or many within the task. It represents the application as a whole.
* Contains information on
  * Resources used by task
  * Networking mode
  * Compatibility (EC2 mode or Fargate)
  * Task Role
    * IAM role that a task can assume
    * Gains temporary credentials within the Task to interact with AWS resources. Best practice way to give ECS tasks permissions.
* The task itself does not scale on its own and is not highly available

Service Definition

* Defines how we want a task to scale
* Can add capacity and add resilience by having multiple independent copies of our task running and controlling restarts, monitoring, etc.
  * Useful for substantial incoming load
* Load balancer can be deployed in front of a service to distribute load over all copies
* Provides scalability and HA

So we create a EC2 cluster and deploy tasks or services within that cluster.
