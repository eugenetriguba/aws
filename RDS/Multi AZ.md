* Only access RDS using the CNAME
* CNAME normally points to the primary instance
* Cannot directly replicate the standby replica using RDS
* Standby replica cannot be used for extra capacity

Synchronous Replication

1. Database writes happen via CNAME at primary instance
1. Primary DB writes these changes to its local storage
1. As that write is happening, the changes are being replicated across to the standby instance.
1. Standby replica commits writes to its local storage.

Creates almost no lag between primary and standby instance.

If error occurs with RDS instance, RDS detects it and changes CNAME to standby replica. Typically, this is done within 60-120 seconds. Multi AZ provides high availability but not fault tolerance.

Main points

* The multi AZ feature is not available with free tier
  * Extra cost for standby replica (generally 2x the cost)
* Standby replica can't be directly used
* Availability improvement, not a performance improvement.
* Multi AZ is within the same region only.
* 60-120 seconds for failover.
* Some performance improvements, such as backups happening on standby replica rather than on the primary DB.
* AZ Outage, Primary Failure, Manual failure, Instance type change and software patching.
