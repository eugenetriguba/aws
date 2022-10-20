# CloudWatch Agent

By default, CloudWatch/CloudWatch Logs doesn't natively capture data inside an instance. For this, CloudWatch Agent is required. This agent also must have the configuration and permissions to be able to send that data in both of those products.

To provide this permission, it is best to create a role with permissions to cloudwatch that is assumed by the instance. Furthermore, we then need to configure which log files to look at to setup log groups/streams.

Long-term, you can potentially use CloudFormation to include that configuration for every instance that is provisioned.
