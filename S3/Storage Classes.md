## S3 Standard

* Object is stored in at least 3 availability zones.
* 11 9s of durability (99.999999999%). For 10,000,00 objects, 1 object loss per 10,000 years.
* Content-MD5 checksums and Cyclic Redundancy checks (CRCs) are used to detect and fix any data corruption.
* When objects are stored a HTTP/1.1 200 OK response is provided by the S3 API Endpoint.
* Billed a 1 GB per month fee for data stored. A $ per GB charge for transfer OUT (IN is free) and a price per 1,000 requests. No specific retrieval fee, no minimum duration, and no minimum size.
* 'milliseconds' first byte latency and objects can be made publicly available.
* S3 standard should be used for frequently accessed data which is improtant and non-replaceable.

## S3 Standard-IA (Infrequent Access)

* Shares most of the architecture and characteristics of S3 standard.
* Storage costs are much cheaper than S3 standard.
* Compromises
  * New cost component: Per GB data retrieval fee, overall cost increases with frequent data access.
  * minimum duration charge of 30 days - objects can be stored for less but the minimum billing always applies.
  * Minimum capacity charge of 128KB per objects.
* Should be used for long lived data that is important or irreplaceable but where data access is infrequent. Don't use it for lots of small files, temporary data, or data that is constantly accessed, or data that is not important or can be easily replaced.

## S3 One Zone-IA

* Cheaper than S3 standard or S3 standard-IA
* Has all compromises of S3 Standard IA
* Additional compromises
  * Data is only stored in one availability zone within the region. Therefore it does not have the multi-AZ resilience model of Standard or Standard-IA. Still get the same level of durability but that is only if the AZ does not fail.
* Should be used for long-lived data, infrequently accessed (retrieval fee), and data that is **non-critical** or data that can be **easily replaced** (replica copies).

## S3 Glacier

* Same 3 availability zone, same durability, and storage cost about 1/5 of S3 standard.
* Objects in S3 stored as "cold" objects (not immediately available and can't be public).
* Any access of data (beyond object metadata) requires a retrieval process.
* Data in glacier is retrieved to S3 Standard-IA temporarily
  * Expedited (1-5 minutes)
  * Standard (3-5 hours)
  * Bulk (5-12 hours)
  * Faster = more expensive
* First byte latency = minutes or hours
* 40KB minimum billable size and 30 day minimum billable duration
* For archival data where frequent or realtime access isn't needed. Minutes-hours retrieval.

## S3 Glacier Deep Archive

* ~1/4 price of Glacier
* Data in a "frozen" state
* 40KB min size and 180 day min duration
* Standard = 12 hours
* Bulk = up to 48 hours
* First byte latency = hours or days (MUCH longer than glacier)
* Archival data that rarely if ever needs to be accessed. Hours/days for retrival e.g. legal or regulation data storage.

## Intelligent Tiering

* Storage class that contains 4 different tiers
  * Frequent access
  * Infrequent access
  * Archive
  * Deep archive
* Don't have to worry about moving objects between tiers.
* System monitors usage of object and moves them between tiers based on usage.
* After 30 days of not being accessed, moves to an infrequent access tier and eventually to archive or deep archive tiers.
* As objects are accessed, they are moved back to the frequent access tier. There are no retrieval fees for accessing objects, only a 30 day minimum duration.
* Monitoring and automation cost per 1,000 objects (management fee)
* Ideal for long-lived data, with changing or unknown patterns.
