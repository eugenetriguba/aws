Highly available, durable, and secure PUB/SUB style notification style (public service).

Coordinate sending and delivery of messages (up to 256KB in size, small files).

SNS topic is where permissions and configuration are defined.
Publisher sends message to topic.
Subscribers by default receive all messages from topic (HTTP/HTTPs endpionts, email, SQS queues, mobile notifications/sms messages, lambda functions ,etc.)

Used across AWS for notifications (e.g. CloudWatch, CloudFormation)

* Delivery Status
* Delivery Retries
* HA and Scalable (Region)
* Server Side Encryption (SSE)
* Cross-Account via TOPIC Policy
