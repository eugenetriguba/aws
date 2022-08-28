Often confused with SQS but are very different products designed for very different situations.

Kinesis = deal with large amount of streaming data ingestion, consumption, and management.

Kinesis is a scalable streaming service (designed to ingest lots of data from lots of applications).

* Public service
* Highly available by design
* Great for things like large scale real time (~200ms) analytics and dashboards.

Producers sent data into a kinesis stream. Stream is the basic identity of kinesis that can scale from low to near infinite data rates.

* Streams store a rolling 24-hour moving window of data. This can be increased to 7 days for additional cost.
* Supports many consumers and producers. Consumers can look at data in different granularity and can access data anywhere in 24 hour window.
* Scales by using a shard architecture
* Each shard allows for 1 MB/s of ingestion and 2MB/s of consumption (more shards = more performance = more cost)
* Stored on shards via Kinesis data records (1MB)

Kinesis Data Firehorse

* Can move data from stream in mass into another AWS data service (for instance, S3)

SQS vs Kinesis

* Is the exam question about the ingestion of data or about worker pools, decoupling, or does it mention asynchronous communication?
* Ingestion of data at scale or large number of devices = Kinesis
* Any others = SQS

SQS

* SQS = 1 production group, 1 consumption group
* Decoupling and Asynchronous communications
* No persistence of messages, no window

Kinesis

* Huge scale ingestion
* Multiple consumers, may be consuming at different rates in rolling window
* Data ingestion, Analytics, Monitoring, App clicks
