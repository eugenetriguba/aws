* NoSQL **Public** DBaaS product - Key/Value & Document
* No self-managed servers or infrastructure
* Manual / Automatic provisioned performance IN/OUT or On-Demand
* Highly Resilient ... across AZs and optionally globally (configured, optional extra).
* Really fast.. single-digit millisecond (SSD based)
* Backups, point-in-time recovery, encryption at rest
* Event-Driven integration...do things when data changes

DynamoDB Tables

* More like DB table as a service product
* A Table is a grouping of ITEMS within the same PRIMARY KEY
* Simple (Partition) or Composite (Partition & Sort) Primary Key
* Each item MUST have a unique value for PK and SK. Can have none, all, mixture, or different attributes. (DDB has no rigid attribute schema).
* Item MAX of 400KB
* Capacity in DynamoDB means speed. Adding capacity means adding speed.
* Capacity (speed) is set on a table.
  * (Writes) 1 WCU = 1KB per second
  * (Reads) 1 RCU = 4KB per second

DynamoDB On-Demand Backups

* Full copy of table
* Retained until removed
* Restore
  * Same region or Cross-region
  * With or without indexes
  * Adjust encryption settings

Point-in-time Recovery (PITR)

* Not enabled by default
* Continuous record of changes allows replay to any point in the window (35 day recovery window)
* 1 second granularity

DynamoDB Considerations

* NoSQL...preference DynamoDB in the exam
* Relational Data...generally NOT DynamoDB
* Key/Value...preference DynamoDB in the exam
* Access via console, CLI, API...'NO SQL'
* Billed based on RCU, WCU, Storage and features on table
