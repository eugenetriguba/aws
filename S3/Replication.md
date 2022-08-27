Allow objects to be replicated between a source and destination bucket in the same or different AWS accounts.

Cross-Region Replication (CRR): Process used when source and destination are in different AWS regions.

Same-Region Replication (SRR): Process used when the buckets are in the same region.

Both types support both same and cross-account replication.

Replication configuration

* Destination bucket
* IAM role that S3 bucket to assume (read objects in source and write to destination)
* All objects or a subset
* Storage class: Default is to maintain same class
* Ownership: Default is the source account (can have destination account own bucket)
* Replication time control (RTC). Guaranteed level of predicability and monitoring on the objects being replicating.

Same account:

* Both S3 buckets are owned by the same AWS account.
* Both trust same AWS account
* Both trust IAM and IAM role
* IAM role automatically has access to source and destination as long as role permission policy grants the access

Cross-Account

* Doesn't trust source account or the role that is used to replicate bucket contents.
* Role isn't by default trusted by destination account.
* Need bucket policy on destination resource policy on destination bucket so the role can write to it.

**Not retroactive** & Versioning needs to be ON
One-way replication source to destination (objects manually added to destination are not added to source).
Unencrypted, SSE-S3 & SSE-KMS (with extra config)
Source bucket owner needs permissions to objects.
No system events, glacier or glacier deep archive.
NO DELETES are replicated to destination

Why use replication?

* SRR - Log Aggregation
* SRR - Prod and Test Sync
* SRR - Resilience with strict sovereignty
* CRR - Global Resilience Improvements
* CRR - Latency Reduction
