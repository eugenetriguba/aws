Logs API actions that affect AWS accounts. If you stop an instance, change a security group, etc., that is all logged.

* Log API call/activities as a CloudTrail event.

* 90 days stored by default in Event History.

* Enabled by default - no cost for 90 day history.

* To customise the service..create 1 or more Trails.

* Management events and Data events.
  
  * Management = "control plane operations"
  * Data = Access to S3 invoke/lambda invoke/etc.
* Default, only management are logged.

* Regional service

* Trail can be set to one region or all regions. Very small number log globally, trail needs to have the global services enabled.

* The services either log to the region the event is generated in or they log to us-east-1 if the service is global.

Exam Powerup

* Denalbed by default.. but 90 days .. no s3
* Trails are how you configure S3 and CWLogs
* Management events only by default
* IAM, STS, CloudFront => Global Service Events (log to us-east-1)
* NOT REALTIME - There is a delay (15 min of the account activity occurring)
