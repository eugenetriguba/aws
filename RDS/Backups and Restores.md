## Key Terms

Recovery Point Objective (RPO)

* Time between last backup and the incident.
* Determines the amount of data lost
* Influences technical solution and cost
* Generally lower values cost more (more frequent system backups, for instance)

Recovery Time Objective (RTO)

* Time between the DR event and full recovery
* Influenced by process, staff, tech, and documentation.
* Generally lower values cost more.

## Types

* Both types use AWS managed S3 buckets to restore the backups (data is region resilient since S3 replicates across AZs in a region).

* Backups occur from *either* the single DB instance if multi-AZ is disabled or the standby instance if multi-AZ is enabled.

* First snapshot is full and next are incremental diffs.

### Automatic Backups

* Just like manual snapshots but automated.
* Occur during backup window that is user defined.
* Retention period from 0 to 35 days (automatically removed after)
* Every 5 minutes, DB transaction logs are stored to S3.
* In effect, this allows you to restore from the snapshot and then replay the db transaction logs on top of the snapshot to get to the state we were in 5 minutes ago.

### Manual Snapshots

* Do not expire (have to delete manually). Even if the RDS instance is deleted!

## Exam Powerup

* Restores create a NEW RDS instance (new DB endpoint address).
* Snapshots = single point in time, creation time
* Automated = any 5 minute point in time
* Backup is restored and transaction logs are "replayed" to bring DB to desired point in time
* Restores aren't fast - Think about RTO
