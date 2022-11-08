# Weighted Routing

Lets you associate multiple resources with a single domain name and choose how much traffic is routed to each resource.

- Can be used when you want a simple form of load balancing or are testing new software versions
- Each record can be given a weight. Then each record is returned based on its weight divided by the total. So if we have a record weighted at "40" and we have a total weight of 100, that record would be returned 40% of the time.
- Records set to 0 are never returned, unless all are set to 0 and then all are considered.
- If a chosen record is unhealthy, the process of selection is repeated until a health record is chosen.

