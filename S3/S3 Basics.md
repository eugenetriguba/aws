Global storage platform - regional resilient

* S3 has ability to tolerate a failure in an AZ and has some ability to replicate data across regions

Public service, unlimited data & multi-user usage of the data.

Perfect for hosting large amounts of data (movies, audio, photos, text, large data sets, etc.)

Economical and can be accessed via a variety of methods (UI/CLI/API/HTTP)

Default storage service for AWS

Objects: Data S3 stores
Buckets: Containers for objects

S3 Objects

* Like files
* Made up of two key components and the metadata
  * Key (similar to a filename, identifies the file in the bucket)
  * Value (data or contents of the object)
    * Can range from 0 bytes to 5TB
  * Also have a Version ID, Metadata, Access Control, and Sub-resources

S3 Buckets

* Created in a specific AWS region (primary home region and never leaves the region unless you configure it otherwise).
* Blast radius of the failure is the region.
* Bucket name is globally unique (across all regions and AWS accounts)
* Holds an unlimited amount of objects
* Flat structure (not like a file system with directories)
* Folders are structured with names.
  * /old/Koala1.jpg would have S3 present a folder in the UI.
  * Folders are often referred to as prefixes to object names
* Containers, stored in a region, most permissions and options are set for S3.

Exam Powerup

* Bucket names are globally unique
* 3-63 characters, all lowercase, no underscores
* Start with lowercase letter or a number
* Can't be IP formatted (1.1.1.1)
* Buckets - 100 soft limit, 1000 hard per account
* Unlimited objects in a bucket (0 bytes to 5 TB)
* Object structure: key = name, value = data

Patterns and Anti-patterns

* S3 is an object store, not file or block (not file system nor can you mount it).
* Great for large scale data storage, distribution, or upload
* Great for offloading data somewhere (can often shrink instances by offloading data to S3)
* INPUT and/or OUTPUT to MANY AWS products
