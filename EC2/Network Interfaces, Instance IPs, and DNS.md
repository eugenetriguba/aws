# Network Interfaces, Instance IPs, and DNS

## EC2 Network and DNS Architecture

- An EC2 instance always starts off with one network interface, an ENI that is considered the primary ENI.
- Optionally, you can also attach one or more secondary ENIs which can be in separate subnets but everything needs to be in the same AZ.
- EC2 is isolated to one AZ.
- The network configuration is attached to the ENI, not the EC2 instance. If you launch a SG around a EC2 instance, it is really around it's ENIs, not the EC2 instance.

### ENI
- Network interfaces have a MAC address that is visible in the OS (the hardware address).
- A Primary IPv4 Private IP
- 0 or more secondary IPs
- 0 or 1 Public IPv4 address
- 1 elastic IP per private IPv4 address
  - Elastic IPs are different than regular public IPv4 addresses (where it is one per interface) in that you can have one public elastic IPv4 address per private IP address on this interface.
- 0 or more IPv6 addresses (by default publically routable)
- Security groups (a SG on an interface will impact all IPs on that interface)
- Per interface, can enable or disable the source/destination check. That means if it is not from one of the IP addresses listed as a source or destined to one of the IP addresses listed as a destination, it will be discarded.

- The capabilities of the secondary ENI is the same as the primary except that you can detach secondary instances and move them to other EC2 instances.

- Private IPs are fixed and come with a private DNS name that resolves to it. If we have a private IP of 10.16.0.10, we would have a DNS name we could use with something like ip-10-16-0-10.ec2.internal

- For public IPs, these are dynamic. When you stop an instance, the public IPv4 address is deallocated and when you start it back up, it will be allocated a new one. However, if you _restart_, it will retain it's same public IPv4 address.

- Public IPs are also allocated a public DNS name such as ec2-3-89-7-127.compute-1.amazonaws.com for the public IP 3.89.7.136. This public DNS name, inside the VPC, will resolve to the private primary IPv4 address of the instance. Outside of the VPC, it will resolve to the public IPv4 address.

- Elastic IPs are associated with the AWS account and can be used with a primary or secondary network interface. If you associate it with the primary interface, then as soon as you do that, the prior public IPv4 is removed and replaced with the elastic IP. It cannot get that prior IP back.

## Exam Powerup

- Secondary ENI + MAC = Licensing
  - Licenses are typically assigned to a MAC address since that is seen as something that will not change. If you attach that to a secondary ENI, you can move that license around EC2 hosts.

- Multi-homed (subnets) Management & Data

- Different Security Groups - Multiple interfaces

- OS - does _not_ ever see the public IPv4

- IPv4 public IPs are dynamic. Stop & Start = change

- Public DNS = private IP in VPC. Public IP everywhere else.
