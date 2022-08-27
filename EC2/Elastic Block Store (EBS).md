* Block Storage
  * Raw disk allocations (volume)
  * Can be encrypted using KMS
* Instances can see block device and create file system on that device (ext3/4, xfs, etc.)
* Storage is provisioned in **ONE AZ**. (Resilient in that AZ)
  * **You cannot communicate across availability zones with storage**
* Attached to \*one EC2 instance (or other service) over a storage network
  * Some allow "multi attach" for clusters. However, the cluster application has to manage it so it doesn't overwrite data.
  * Generally good to think about EBS volumes as things attached to one instance at a time.
* Can be detached and reattached, not lifecycle linked to one instance. Persistent.
* Snapshot (backup) in (snapshots are regionally resilient, replicated across AZs in that region). Can use that snapshot to create a new volume from snapshot (useful when wanting to migrate between AZs). These snapshots are stored in S3 and that is where the replication comes from across the AZs. These snapshots can even be copied to S3 buckets in other regions for global resilience.
* Different physical storage types, different sizes, different performance profiles.
* Billed based on GB-month (and in some cases performance)
* EBS replicates **within an AZ**. Failure of an AZ means failure of a **volume**.
