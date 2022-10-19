# Dedicated Hosts

[Pricing](https://aws.amazon.com/ec2/dedicated-hosts/pricing/)

Allows you to gain access to hosts dedicated for your use which you can then use to run EC2 instances.

## Overview

- Designed for a specific family of instances (i.e. a1, c5, m5, etc.)
  - Nitro-based virtualized hosts are more flexible.
- No instance charges. You pay for the host and its capacity and you pay for that capacity in its entirety.
- On-Demand or reserved options are available for payment.
- Host hardware has physical sockets and cores.
  - Dictates how many instances can be running on that host
  - Software which is licensed based on physical sockets or cores can utilize this visibility of the hardware.

## Use case

Generally, this is used for applications which use software that have physical core/socket licensing.
