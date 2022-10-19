# Enhanced Networking & EBS Optimized

## Enhanced Networking

Designed to improve the overall performance of EC2 networking. It is required for any high-end performance features.

- Uses SR-IOV (NIC is virtualization aware).
  - Rather than handling virtualization in software, the hardware is aware of it.

- Higher I/O and lower host CPU usage
- More bandwidth
- Higher packets-per-second (PPS)
- Consistent lower latency

## EBS Optimized

EBS = block storage over the network
- Historically network was shared, data and EBS.

EBS Optimized means dedicated capacity for EBS. For most instances, they support and have it enabled by default. For some older instances, it is supported but enabling it costs extra.

- Set on a per instance basis
