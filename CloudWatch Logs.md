* Public Service - usable from AWS or on-premises.
* Store, monitor, and access logging data.
* AWS Integrations - EC2, VPC Flow Logs, Lambda, CloudTrail, R53, and more.
* Security for these integrations is generally provided by IAM or service roles.
* Can generate metrics based on logs - metric filter
  * These metric filters can generate metrics which can then trigger alarms to notify AWS or external systems to take action.
* Via logging sources, we have log events that are generated which go into log streams. These log streams can be grouped together via log groups which define the retention and permission settings.

Unified cloudwatch agent is for logging outside of AWS products or services into cloudwatch.
