* Architecture is *very* different from RDS
* Uses a "Cluster"
  * Contains a single primary instances + 0 or more replicas
  * Replicas can be used as read replicas *and* standby replicas.
  * No local storage, uses shared cluster volume.
    * Faster provisioning, improved availability, and performance.

Storage

* Shared storage that is SSD based
  * High IOPS, low latency
* Max volume of 128 TiB, 6 Replicas, AZs
* Replication happens at storage level, not the db instance.
* Primary instance can read/write and replicas can read.
* Up to 15 replicas with any one of them able to be the failover
* Storage is billed based on what is used
* High water mark - billed for the most used that month
  * \*is being changed
* Storage which is freed up can be re-used
* If you need to reduce costs from storage used, you can remove unnecessary storage and migrate data to a new cluster from the old cluster.
* Replicas can be added and removed without requiring storage provisioning

Endpoints

* Cluster endpoint
* Reader endpoint
