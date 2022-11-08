# Multi Value Routing

Multivalue answer routing lets you configure R53 to return multiple values, such as IP addresses for your web servers, in response to DNS queries. You can specify multiple values for almost any record, but multivalue answer routing also lets you check the health of each resource, so Route 53 returns only values for healthy resources.

- Up to 8 'healthy' records are returned. If more exist, 8 are randomly selected.
- Supports multiple records with the same name
- Any records which fail health checks won't be returned when queried
- Each record is independent and can have an associated health check
- Client chooses and uses 1 value

Multivalue routing aims to improve availability. You can use it if you have multiple resources that can serve requests and you want to select one at random. However, it is _not_ a substitute for a load balancer, which handles the actual connection process.

Simple routing = no health checks and generally used for a single resoruce
Failover = often used for active backup architectures, with S3 commonly used as a backup
Multivalue = many resources that can all service requests and are all health checked

