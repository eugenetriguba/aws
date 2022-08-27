Often confused for SQS but they are very different products designed for very different situations.

* Kinesis is a scalable streaming service
  * Designed to ingest lots of data from lots of different applications or devices.
* Producers send data into a kinesis stream.
* A producer is the basic entity of a stream.
* Streams can scale from low to near infinite data rates.
* Public service and highly available by design.
* Streams store a 24-hour moving window of data (includes persistant storage for 24 hour period)
* Supports multiple producers to the stream and multiple consumers from the stream. Each consumer can access any data within that 24 hour window.
