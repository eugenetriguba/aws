* EC2 instances are virtual machines (OS + Resources)
* EC2 instances run on EC2 Hosts (physical hardware)
* Shared Hosts
  * Shared across AWS customers
  * Price based on how run they are long and what resources are allocated
  * No interaction with other instances, even if running on same physical host.
* Dedicated Hosts
  * Paying for the entire host
  * Don't share it with any other AWS customers
  * Don't pay for any instances running on it
* AZ resilient
  * Hosts = 1 AZ
  * If AZ fails, Host fails and therefore, instances fail.
  * Have to assume at least some or all of instances running in AZ will fail if AZ fails or be heavily impacted.
* Instance Store
  * Temporary
* Networking
  * Storage
  * Data Network
* *Very* reliant on the AZ it is in.
* Instances stay on the host unless
  * Host fails or is taken down for maintenance
  * Instance is stopped and then started (different than restart). However, that host will still be in the same AZ. To migrate to different AZ, you essencially create a copy and recreate it in a different AZ.

#### What is EC2 Good for?

* Traditional OS+Application Compute need
* Long-Running Compute
* Server-style applications
* Either burst or steady-state load
* Monolithic application stacks
* Migrated application workloads or Disaster Recovery
