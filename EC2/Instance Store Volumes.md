* Block Storage Devices
* Physically connected to one EC2 Host
* Instances on that host can access them
* Highest storage performance available in AWS because they are locally attached (much higher than EBS)
  * D3 = 4.6 GB/s throughput
  * I3 = 16 GB/s of sequential throughput
  * More IOPS and Throughput vs EBS
* Included in instance price
* ATTACHED AT LAUNCH. Can't attach them afterwards.
  * You can choose to use them or not. But if you don't, you can't adjust it later.

An instance store provides temporary block-level storage for your EC2 instance. This storage is located on disks that are physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as load-balanced pool of web servers.

An instance store consists of one or more instance store volumes exposed as block devices. The size of an instance store as well as the number of devices available varies by instance type.

The virtual devices for instance store volumes are ephemeral\[0-23\]. Instance types that support one instance store volume have ephemeral0. Instance types that support two instance store volumes have ephemeral0 and ephemeral1 and so on.

Exam Powerup

* Local on EC2 Host
* Add at launch ONLY
* Lost on instance move, resize, or hardware failure
* High performance
* You pay for it anyway - included in the instance price
* TEMPORARY
