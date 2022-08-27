Decides between how much AWS manages and how much you manage.

EC2 Mode

* Responsible for EC2 hosts that is running the containers
* Need to be aware of and manage capacity of the cluster

Fargate Mode

* No servers to manage
* Uses Fargate Shared Infrastructure
* Tasks are injected from shared infrastructure into the VPC with an elastic network interface. It has an IP address from within the VPC. It can be accessed from within the VPC or the public internet if the VPC is configured so.
* Can deploy into a new VPC or a custom VPC.
* Only pay for the containers that you're using and the resources that they consume. No visibility of any host costs or think about capacity/availability.

EC2 (VMs) vs ECS (EC2) vs ECS (Fargate)

* If you use containers, use ECS.
* Large workload and price conscious, use EC2 mode.
  * Probably be cheaper but only if you can minimize the admin overhead for them.
* Large workload and overhead conscious, use Fargate.
* Small / burst workloads, use Fargate.
  * Makes most sense since you only pay for the capacity you use rather than having EC2 Hosts running constantly.
* Batch / Periodic workloads, use Fargate.
