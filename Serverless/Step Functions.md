Long-running Serverless Workflows

Problems with Lambda

* 15-minute max execution time
  * Can be chained together (but messy at scale)
* Runtime environments are stateless

Step functions let you create state machines.

* Start -> states -> end
* States are things that occur
* Max duration of 1 year for execution
* Standard and express workflows
  * Standard is the default and has 1 year execution limit
  * Express is designed for high volume, event processing workflows. They can run up to 5 minutes.
* Started via API Gateway, EventBridge, Lambda, etc.
* Amazon States Language (ASL) - JSON Template
* IAM Role is used for permissions (assumed role while running)

States

* Succeed & Fail states
* Wait (certain period of time or until specified date and time)
* Choice (always state machine to take different path based on input)
* Parallel
* Map (accepts list of things and does something for each item)
* Task (Lambda, Batch, DynamoDB, ECS, SNS, SQS, Step Functions, etc.)
