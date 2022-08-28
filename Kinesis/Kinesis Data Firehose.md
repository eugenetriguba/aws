* Fully managed service to load data for data lakes, data stores, and analytics services.
* Automatic scaling, fully serverless, and resilient.
* Supports transformation of data on the fly (lambda).
* Billing - volume through firehose.

## What problem does it solve?

Kinesis streams have no way of persisting the data past their rolling window. So Kinesis Data Firehose can move that data out into somewhere else.

## Where can it deliver data?

* HTTP Endpoints
* Splunk
* Redshift (Uses S3 bucket intermediary)
* ElasticSearch
* S3

## How does it receive data?

* Directly from producers
* From a kinesis data stream.

## How often is delivery to the destination?

* Near real-time, whenever the buffer size reaches 1 MB or the buffer interval of 60 seconds passes.

## What are the use cases?

* Persistence to data to kinesis data stream
* Store data in a different format
* Delivery data to one of the supported products
