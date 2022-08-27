* ACID and BASE are DB transaction models

* CAP Theorem - Consistency, Availability, Partition Tolerant (resilience) - Choose 2
  
  * Consistency: Every read to a DB will receive the most recent write
  * Availability: Every request will receive a non error response but w/o guarantee it contains most recent data
  * Partition Tolerant: System can be made of multiple network partitions and the system continues to operate even if there are a number of dropped messages or errors between these network nodes
* ACID = Consistency
  
  * Atomic
    * Either all part or no components of a transaction succeeds or fails
  * Consistent
    * Transactions move the database from one valid state to another. Nothing in-between is allowed.
  * Isolated
    * If multiple transactions occur at once, they don't interfere with each other. Each executes as if it's the only one.
  * Durable
    * Once committed, transactions are durable. Stored on non-volatile memory, resilient to power outages or crashes.
  * If ACID is mentioned, likely referring to RDS DBs. Limits ability to scale.
* BASE = Availability
  
  * Basically available
    * READ and WRITE operations are available "as much as possible" but without any consistency guarantees - kinda, maybe
  * Soft State
    * The database doesn't enforce consistency. This is offloaded onto the application/user.
  * Eventually Consistent
    * If we wait long enough, reads from the system will be consistent
  * Highly scalable and can deliver really high performance
  * DynamoDB\* 
    * Normally works in BASE like way
    * Offers eventually and immediate consistent reads
    * Offers ACID features like DDB transactions
    * BASE on exam = nosql style DB
    * NoSQL/DDB and ACID, may be referring to DDB transactions.
