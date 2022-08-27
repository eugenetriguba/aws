# Aurora Global Database Product

Global databases allow you to create global level replication using Aurora from a master region to up to five secondary AWS region.

Primary Region
 - Offers similar functionality to an Aurora Cluster
 - 1 RW instance and up to 15 RO replicas in that cluster

Global databases introduce the concept of secondary regions.
 - Up to 16 replicas that are all RO.
 - Replication from primary to secondary happens at the storage layer and typically within 1 second from primary to all secondaries.
 - Application can use the primary instance in the primary region for write operations and then the replicas in the primary or secondary regions for read operations.

## When to use global databases?

- Cross-Region disaster recovery and business continuity
 - Secondary cluster can act as primary cluster in event of a disaster in the primary region.
 - RPO and RTO are both really low because of 1s replication time between primary and secondary regions.

- Global Read Scaling - low latency performance improvements

- ~1s or less replication between regions.
 - 1 way replication between primary to secondary

- No impact on DB performance because it happens at the storage layer.

- Secondary regions can have 16 replicas that can be promoted to RW if a disaster occurs.

- Currently a MAX of 5 secondary regions.


