* Persistence -> EBS (avoid instance store)

* Resilience -> EBS (avoid instance store)

* Storage isolated from instance lifecycle -> EBS

* Resilience w/ App in-built replication ... it depends

* High performance needs ... it depends

* Super high performance needs -> Instance Store

* Cost -> Instance Store (it's often included)

EBS (Try to memorize)

* Cheap = ST1 or SC1
* Throughput or streaming -> ST1
* Unless Boot needed, NOT ST1 or SC1
* GP2/3 up to 16,000 IOPS
* IO1/2 - up to 64,000 IOPS (\*256,000 via IO2 Block Express)
* RAID0 + EBS up to 260,000 IOPS (io1/2-BE/GP2/3)
  * Max IOPS per instance
* more than 260,000 IOPS -> Instance store
