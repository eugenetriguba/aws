* Need to enable logging on source bucket
* Logging is managed by S3 Log Delivery Group. Needs access to source and target.
* Best effort log delivery, accesses to source bucket are usually logged in target bucket within a few hours.
* Log files consist of log records and records are newline-delimited. Attributes are space delimited.
* Single target bucket can be used by many source buckets.
* Detailed information about the request about the source bucket
  * Security and any access audit
  * Understanding charges and access patterns of customers
  * Need to manage lifecycle and deletion of any log files
