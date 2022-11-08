# Failover Routing

Failover routing lets you route traffic to a resource when the resource is healthy or to a different resource when the first resource is unhealthy.

- Allows for multiple records of the same name (primary and a secondary)
- Key element is the inclusion of a health check. It generally occurs on the primary record and if it is health, it resolves to the value of the primary record. If it fails its health check, then the queries return the secondary record of the same name.

A common architecture is to use failover for a "out of band" failure/maintenance page for a service.
- Use when you want to configure active/passive failover.

