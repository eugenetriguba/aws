EC2 (Elastic Compute Cloud) provides access to virtual machines known as “instances”.

* Provision VMs with resources and operating system of your choosing.
* “Should be” the default starting point for any compute requirement in AWS.

EC2 Features

* IAAS (Infrastructure as a Service, manage OS and up)
* Unit of consumption: Instance (Virtual Machine, an OS configured in a certain way with a certain set of resources).
* Private service by default - uses VPC networking.
* If you want public access to the instance, then the VPC it is running in needs to support public access.
* AZ Resilient (Instance fails if AZ fails because it is launched into a particular subnet which is in a particular availability zone).
* Instances come in different sizes and capabilities (advanced storage, GPUs, networking, etc.).
* On-Demand Billing (per second, pay for resources you consume)
  * Charge for running, storage, and extras for commercial software the instance is run with.
* Storage
  * Local on-host storage
  * Elastic Block Store (EBS)
* Instance Lifecycle
  * Running, Stopped, Terminated (one way change, cannot undo)
  * States influence the charges for the instances.
  * When running, CPU, Memory, Network, and long-term storage charges all apply. However, when stopped, only the long-term storage charge applies.
  * To have no EC2 cost, we need to terminate it. However, it is not reversible.
* Amazon Machine Image (AMI)
  * Image of an EC2 instance.
  * Can be used to create an EC2 instance or can be created from an EC2 instance.
  * Contains
    * Permissions (which account can use the image)
      * Public (everyone allowed)
      * Owner (implicit allow, basically private)
      * Explicit (specific AWS accounts allowed)
    * Root Volume (drive that boots the OS)
    * Block Device Mapping (links volumes to the AMI and how they are presented to the OS)
* Connecting
  * Windows
    * RDP (remote desktop protocol on port 3389)
  * Linux
    * SSH (port 22)
    * SSH keypair (private is for you and a copy of the public goes on the instance)
