# Database Migration Service (DMS)

DMS is a managed service which allows for 0 data loss, low or 0 downtime migrations between 2 database endpoints.

- Managed database migration service
- Runs using an EC2 replication instance that runs one or more replication tasks
- Source and destination endpoints to point at source and target databases.
- One endpoint MUST be on AWS (can be used for two on-premise databases)

Jobs
- Full load (one off migration of all data)
- Full load + CDC (Change data capture) for ongoing replication which captures changes
- CDC only (if you want to use an alternative method to transfer the bulk DB data, such as native tooling)

SCT (Schema Conversion Tool) can assist with Schema Conversion to different databases.

DMS is a useful tool to migrate from on-prem to AWS.

## SCT

- Standalone tool.
- Used when converting one database engine to another.
- Including DB -> S3 (Migrations using DMS)
- SCT is not used when migrating between DB's of the same type
- On-prem MySQL -> RDS MySQL, SCT would not be used.
- Works with OLTP DB Types (MySQL, MSSQL, Oracle) and OLAP (Teradata, Oracle, Vertica, Greenplum..)
- e.g. On-premises MSSQL -> RDS MySQL
- e.g. On-premises Oracle -> Aurora

## DMS & Snowball

- Larger migrations might be multi-TB in size
- moving data over networks takes time and consumes capacity
- DMS can utilize snowball
- Step 1: Use SCT to extract data locally and move to a snowball device.
- Step 2: Ship the device back to AWS. They load it onto an S3 bucket.
- Step 3: DMS migrates from S3 into the target store.
- Step 4: Change data capture (CDC) can capture changes and via S3 imtermediary they are also written to the target database.

