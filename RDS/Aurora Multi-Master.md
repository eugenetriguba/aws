# Aurora Multi-Master

- Default Aurora mode is Single-Master

- One R/W and 0+ Read Only Replicas

- Cluster Endpoint is used to write, read endpoint is used for load balanced reads.

- Failover takes time - replica promoted to R/W

- In Multi-Master mode, **all instances** are R/W.

- Multiple Aurora provisioned instances also exist in the cluster.

## Differences

- No cluster endpoint to use. Applications are responsible for connecting to instances in the cluster.

- No load balancing across instances with a multi-master cluster.

- When one of the R/W nodes recieves a write request from the application, it immediately proposes that data be committed to all the storage nodes in that cluster. Each node then either confirms or rejects. IT rejects it if it conflicts with someone already in flight. The writer instance is looking for a quorum of nodes to agree so it can commit the change to the shared storage. If it can't, it cancels the operation and emits an error to the application.

- The change, if made, is then replicated across the clusters and has their in-memory caches updated.

## Aurora Single-Master

We have a cluster endpoint and if the primary RW node fails, the cluster will notice it and failover to the RO replica. However, this failover can take time. And the configuration to make one of the replicas the new primary RW node is not immediate and can cause disruptions.

## Aurora Multi-Master

An application can connect to one or both (if two) writer instances. If one of those instances fails, the writes would still go to the second RW instance. Using an Aurora Multi-Master setup is one component in building a fault tolerant application.

- Better and faster availability
- Failover can occur within app
- Can immediately send write operation to the other writer

- Application needs to manually handle load balancing across the instances
