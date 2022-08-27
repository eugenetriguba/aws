# VPC Routing and Internet Gateway

- Every VPC has a VPC Router (and is a highly available. It runs in all the AZs that the VPC uses).
- In every subnet, the network + 1 address.
- If an EC2 instance from one subnet wants to communicate to an EC2 instance from another subnet, the VPC router is what routes traffic between the subnets.
- Controllable by "route tables" which determines what to do with traffic when it leaves the subnet. Each subnet has a route table.
  - The route table that is associated with a subnet defines what the VPC router will do when data leaves that subnet.
  - VPC is originally created with a "main route table" and if you don't explicitly associate a custom route table with a subnet, it uses the default.
  - A subnet can only have one route table associated with it but many subnets can be associated with a route table.

Route table
 - List of routes
 - The routes can match a single IP or an entire network of which that IP is part of.
 - The route could also be a default route (0.0.0.0, i.e a catch all).
 - If there are multiple matches, the more specific route (the higher prefix value) wins out.
 - All route tables have at least one entry with the VPC CIDR range that tells the route that all traffic within the VPC is local and can be delivered directly. If the VPC is IPv6 enabled, it'll have another entry for the IPv6 local route for the VPC. These local routes can never be updated and always take priority.

Route tables are attached to 0 or more subnets.
A subnet has to have a route table.
It's either the main route table of the VPC or a custom one.
Route table determines what happens to data when it leaves that subnet or subnets when it leaves that route table it is associated with.
Local routes are always there and match the IPv4/IPv6 CIDR range and always take priority.
For anything else, higher prefix values are more specific and take priority.
The way that a route works is that it matches a destination IP and for that route, directs traffic towards a specific target.

## Internet Gateway

- **Region resilient** gateway attached to a VPC.
- 1 VPC = 0 or 1 IGW
- 1 IGW = 0 or 1 VPC
- Valid for all AZs that the VPC uses.
- Runs from within the AWS Public Zone.
- Gateways traffic between the VPC and the Internet or AWS Public Zone (S3, SQS, SNS, etc.).
- Managed - AWS handles the performance.

1. Create IGW
2. Attach IGW to VPC
3. Create custom RT
4. Associate RT with web subnet
5. Default Routes => IGW
6. Subnet allocate IPv4 and optionally IPv6 by default

Public IPv4 addresses never touch the actual services inside a VPC. Instead, when you allocate a public IPv4 address, a record is created that the IGW maintains. It links the instance's private IP with the public IP. The instance itself is not configured with the public IP (so the OS on an EC2 instance would only see the private IP).

## Bastion Host / Jumphost

- Bastion Host = Jumphost
- An instance in a public subnet.
- Incoming management connections arrive there.
- Then access internal VPC resources.
- Often the only way IN to a VPC.

