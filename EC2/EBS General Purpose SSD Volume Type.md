General Purpose SSD - GP2

* Volumes can be as small as 1GB or as large as 16TB.
* An IO Credit is 16KB
* IOPS assume 16KB
* 1 IOPS is 1 IO in 1 second
* IO 'Credit' Bucket Capacity has 5.4 million IO Credits. Fills at rate of Baseline Performance.
* Bucket fills with min 100 IO credits per second, **regardless of volume size**.
* Beyond the 100 minimum, the bucket fills 3 IO credits per second, per GB of volume size (Baseline Performance).
* Can burst up to 3,000 IOPS by depleting the bucket.
* All volumes get an initial 5.4 million IO credits. 30 minutes @ 3000 IOPS. Great for boots and initial workloads.
* For volumes larger than 1TB, Baseline is above burst. Credit system isn't used. You always achieve the Baseline. Up to a maximum for GP2 for 16,000 IO credits per second (Baseline performance).
* Great for boot volumes, low-latency interactive apps, and dev/test environments.

GP3

* Every volume, regardless of size, starts with 3,000 IOPS & 125 MiB/s - STANDARD
* Cheaper than GP2 (~20% base price)
* Extra cost for up to 16,000 IOPS or 1,000 MiB/s
* 4x Faster Max throughput vs GP2 - 1,000 MiB/s vs 250 MiB/s
* Great for virtual desktops, medium sized single instance databases, low-latency interactive apps, dev and test environments, and boot volumes.
