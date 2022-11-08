# Latency-Based Routing

If your application is hosted in multiple AWS regions, you can improve performance for your users by serving their requests from the AWS region that provides the lowest latency.

- Should be used when you are trying to optimize for performance and user experience.
- AWS maintains a database of latency between the users general location and the regions tagged in records
- Latency-Based routing supports one record with the same name in each AWS region

