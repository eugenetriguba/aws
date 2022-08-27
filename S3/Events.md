* Notification generated when events occur in a bucket
* Can be delivered to SNS, SQS, and Lambda functions
* Object Created (Put, Post, Copy, CompleteMultiPartUpload)
* Object Delete (\*, Delete, DeleteMarkerCreated)
* Object Restore (Post (initiated), Completed)
* Replication (OperationMissedThreshold, OperationReplicatedAfterThreshold, OperationNotTracked, OperationFailedReplication)
* Need event notification configuration on bucket. As those actions happen, events are generated and sent to the destination. The destination needs resource policies that allow S3 to interact with them.
* EventBridge is an alternative and supports more types of events and more services. Default to EventBridge unless there is a specific reason not to do so.
