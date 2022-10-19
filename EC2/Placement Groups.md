# Placement Groups

[Placement Groups User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

Normally when you launch an EC2 instance, it's physical location is selected by AWS, placing it on whatever EC2 host makes most sense in the AZ it is launched in. Placement groups allow you to influence placement so that they can be either physically close together or not.

## Types

### Cluster Placement Groups (Performance)

This placement group is used when you want to achieve the absolute highest level performance within EC2 by packing instances together.

With them, you create the group and normally want to launch all the instances that will be in the group at the same time and all of the same type. This is so that AWS allocates capacity in a suitable location for everything you require. For instance, if you launch 9 instances and you're allocated into an area that has capacity for 12 then if you later want to double your instances, it will be more difficult to do so.

Because of their performance characteristic, cluster placement groups need to be launched into a single AZ.

The idea here is that all of the instances within a cluster placement group generally use the same rack and even the same host. They have fast direct bandwidth to all the other instances inside that same group.

- Can achieve 10Gbps p/ stream rather than the 5Gbps normally.
- Lowest latency and maximum packets per second in AWS.

Now, to achieve these levels of performance, you need to be using instances with high performance networking. So more bandwidth than the 10GB p/s single stream and also using enhanced network on all instances.

#### Highlights

- Highest level of throughoutput and lowest latency in AWS.
- However, because of the physical location, if the hardware they are running on fails, it could take down all the instances within that cluster placement group so this placement group offers little to no resilience.

#### Constraints

- Can't span AZs. ONE AZ ONLY and locked in when launching first instance.
- Can span VPC peers but significantly impacts performance in a negative way.
- Requires a supported instance type
- Generally should use the same type of instances (not mandatory but for best results)
- Launch at the same time (not mandatory again but very much so recommended)

#### Use case

- Performance
- Fast speeds
- Low latency

### Spread Placement Groups (Resilience)

This type of placement group is designed to ensure the maximum amount of availabilty and resilience for an application.

They can span multiple AZs. The instances are located on separate isolated infrastructure racks within each AZ (distinct racks and power supplies for any other instance). This means if a single rack fails, the fault will be isolated to one of those racks and therefore, to only one instance.

#### Highlights

- Provides infrastructure isolation.
- Each INSTANCE runs from a different rack.
- Each rack has its own network and power source

#### Constraints

- 7 instances per AZ (isolated infrastructure limit).
- Not supported for dedicated instances or hosts

#### Use case

- Small number of critical instances that need to be kept separated from each other

### Partition Placement Groups (Topology Awareness)

This placement group is designed for when you have infrastructure where you have more than 7 instances per AZ, but you still need the ability to separate those instances into separate fault domains.

They are spread across multiple AZs. When creating, you specify a number of "partitions" with a MAX of 7 per AZ. With each partition, it has its own rack, networking, and power.

This is similar to spread placement groups, however, with partition placement groups you can launch as many instances as you want within the partitions and you or AWS can choose which partitions to place them in.

This type of placement group is designed for huge scale parallel processing systems, where you need to create groupings of instances and have them separated. Then you as the designer can have control which instances are in the same or different partitions. You can also share this information with topology aware applications (such as HDFS, HBase, and Cassandra) so that they can make intelligent data replication decisions.

#### Highlights

- Instances can be placed in a specific partition (or auto placed)
- Contain the impact of failure to part of an application

#### Constraints

- 7 instances per AZ

#### Use case

- Great for topology aware applications
