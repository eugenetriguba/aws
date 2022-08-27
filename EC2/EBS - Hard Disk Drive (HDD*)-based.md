st1 - Throughput Optimized

* Cheap (less expensive than SSD)
* Not great for random access
* Throughput and economy more important than IOPS and extreme levels of performance
* 125 GB to 16 TB
* Max 500 IOPS (IO measured as 1 MB blocks). Max 500 MB/s
* 40 MB/s/TB Base
* 250MB/s/TB Burst
* Designed for when cost is a concern but need frequent access and throughput intensive sequential data
* Big data, data warehouses, log processing.

sc1 - Cold HDD

* Cheaper than st1 but comes with tradeoffs
* Maximum of 250 IOPS (1 MB IO Size). Max 250 MB/s
* 12 MB/s/TB Base
* 80 MB/s/TB Burst
* 125GB to 16 TB
* Lowest cost HDD volume designed for less frequently accessed workloads
* Colder data requiring fewer scans per day
