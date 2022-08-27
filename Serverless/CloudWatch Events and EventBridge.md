Can provide near real-time stream of system events.

* If X (supported service that generates event, i.e. producer) happens, or at Y time(s) (unix cron format)... do Z (supported target service for event, i.e. consumer)
* EventBridge = CloudWatch Events v2
* A default event bus for the account (stream of events for any supported service for that AWS account).
* In CloudWatch Events, this is the only bus (it is implicit).
* EventBridge can use additional event buses.
* Rules can be created that match events (or schedules) and that events can then be routes to 1 or more targets (i.e. Lambda).

Default account Event bus

* Stream of events for any supported service for that AWS account
* i.e. EC2 instance state change causes event to run through the event bus. EventBridge will then monitor these events and use rules (linked to specific bus).
* Rules can be pattern matching rules or schedule rules and route the event to a target.
* Events are simply JSON structures.
