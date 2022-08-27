# DynamoDB Operation

## Reading and Writing

### Types

#### On-Demand

Useful for when you have an unknown or unpredictable workload. You don't have to explicitly set capacity settings so this would lead to a lower admin overhead.

Charged price per million R or W units (can be up to 5x the price of provisioned capacity so you pay for the flexibility).

#### Provisioned

Set Read Capacity Units (RCU) and Write Capacity Units (WCU)
Every operations consumes at least 1 RCU/WCU(\*)
1 RCU is 1 x 4KB read operation per second (\*) (1KB rounds up to 4KB)
1 WCU is 1 x 1KB write operation per second
Every table has a RCU and WCU burst pool (300 seconds)

### Operations

#### Query

Query i.e. way to retrieve data from the product.

This operation accepts a single PK (partition key) value and _optionally_ an SK (sort key) or range. Capacity is the size of _all returned items_. Further filtering discards data - capacity is still consumed.

We can _only_ query on PK or PK and SK.

With DDB, it is always more efficient to return multiple items in a single operation. For instance, let's say we need to retrieve two items: 1 is 2.5K and another is 1.5K. If we retrieve them separately, we would have used up 2 RCUs. However, if we retrieve them both at once, we would have only used 1 RCU.

Generally with DDB, we're reading and writing entire items. So there is an architectural benefit with the platform to reduce the size of item as much as possible. As a minimum, we would be using up the capacity that the whole item takes.

If we want to pick a particular subset of SK values, we're only charged for the response. If we want to filter to only get particular items from the query, we are still charged for the entire item and the other attributes are just tossed out.

If we wanted to perform a search across the entire table (look for every entry with X attribute), we can't do that with the query operation.

#### Scan

Least efficient operation with DDB if you want to get data (expensive) but it is also the most flexible.

SCAN will move through a table consuming the capacity of every item. You have complete control on what data is selected, any attributes can be used and any filters applied but SCAN consumes capacity for every item scanned through.

## Consistency

Eventually consistent or immediately consistent.

When new data is written to the database and that data is immediately read, is that read data the same as the new data that was written? Or is it only eventually the same?

Eventually consistency is easier to implement and scales better.
Strong consistency is necessary is some types of applications or operations but it is more costly to achieve and doesn't scale as well.

With DDB, every piece of data is replicated in separate AZs. Each one of those points is called a storage node and out of those three storage nodes in three AZs, one of them is elected a "leader". If the leader ever fails, a new one is chosen.

Writes are sent to the leader node so it will receive the update first. The leader node is then known as consistent. Writes are more expensive because they always have to occur on the leader storage node and so they can't scale as well as reads.

Once the leader node gets the write, it starts the process of replication. Typically, this finishes within a few milliseconds.

Reads: eventually and strongly consistent.

1 RCU is 4KB of data read from DDB read every second but that is using _strongly_ consistent reads. Eventually consistent reads are half the price.

Eventual consistent reads check 1/3 nodes - could be unlucky with stale data if a node is checked before replication completes. 50% of the cost vs. strongly consistent.

Strongly consistent reads connect to the leader node to get the most up-to-date copy of the data.

Not every application or access type tolerates eventual consistency. Select the model as appropriate.

## WCU Calculation

If you need to store 10 items per second, 2.5K average size per item.

Calculate WCU per item: ROUND UP(ITEM SIZE / 1KB) (=3)
Multiply by average of writes per second (=30)

Total (=30 for this example)

WCU = 1K in size

## RCU Calculation

If you need to retrieve 10 items per second, 2.5K average size.

Calculate RCU per item: ROUND UP(ITEM SIZE / 4KB) (=1)
Multiple by average read operations per second (=10)
Total strongly consistent RCU required (=10 for this example)

(50% of strongly consistent) = Eventually consistent RCU required (=5)


