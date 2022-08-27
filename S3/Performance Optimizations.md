## Single PUT Upload

* By default, uploads as a single data stream to S3 via s3:PutObject.
* If a stream fails, the entire upload fails and it requires a full restart.
* Speed & reliability = limit of 1 stream
* A single PUT upload is limited to 5GB in size (however, with a single stream of data, would likely be unreliable at this size).

## Multipart Upload

* Data is broken up
* Minimum data size 100MB for multipart
* 10,000 max parts, 5MB -> 5GB
* Last part can be smaller than 5MB
* Individual parts can fail and be restarted rather than the entire whole.
* Transfer rate = speeds of all parts (better transfer rates by splitting into small bits and uploading in parallel)

## S3 Accelerated Transfer

* Default off
* Problem: Using the public internet for data transfer is never an optimal way to get data from source to destination. We have no control over how that traffic is routed. The public internet is not designed primarily for speed, rather for flexibility and reliability.
* Public internet is used to communicate with Edge locations (which are really close) and then the edge location uses the AWS Global network. It is much faster and has lower consistent latency.
* Restrictions: bucket name cannot contain periods and needs to be DNS compatible in its naming.
* Creates a new endpoint for the bucket to utilize the transfer acceleration feature which needs to be used to utilize the feature.
* See s3-accelerate-speedtest for a speed comparison on each region with the feature neabled.
