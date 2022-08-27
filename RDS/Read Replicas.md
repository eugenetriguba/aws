* Read-only replicas of RDS instance
* Unlike Multi AZ where you can't directly use the standby replica for anything, you can use read replicas but only for read operations.
* Separate DB endpoint address and kept in sync with asynchronous replication.
* Can be created in same region or different regions.
* Cross-region read replicas, AWS handles all networking/configuration and is fully encrypted in transit.
* Up to 5 read replicas
* Only thing that really provides scaling in terms of RDS instances

## Why read-replicas?

### Performance

* 5x direct read-replicas per DB instance
* Each providing an additional instance of read performance
* Can easily scale read performance
* Read-replicas can have read-replicas but lag starts to be a problem
* Global performance improvements

### Availability Improvements

* Snapshots & Backups improve RPO
* RTO's are still a problem
* RR's offer near 0 RPO
* RR's can be promoted quickly - low RTO
* Failure only - watch for data corruption
* Read only - until promoted
* Global availability improvements...global resilience.
