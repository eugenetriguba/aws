# Network Address Translation (NAT) and NAT Gateways

NAT Gateways are AWS's implementation of NATs.

## What is NAT?

- Network Address Translation (NAT)

- Set of processes which allow remapping source or destination IPs.

- The internet gateway implements static NAT which maps private IP to public IP on outgoing connections and public IP to private IP on incoming connections.

- IP masquerading: hiding CIDR blocks behind one IP. Many private IPs to one single IP.
  - This is popular because the public IPv4 address space is running out.
  - Gives private CIDR range **outgoing** internet access
  - These private IPs masquerade behind the IP address of the NAT gateway.

## NAT Gateways

- Runs from a public subnet
- Uses Elastic IPs (Static IPv4 Public)
- AZ resilient Service (HA in that AZ)
- For region resilience, need a NATGW for each AZ and then have a RT in each AZ with that NATGW as the target.
- Managed, scales to 45 Gbps, billed on duration (standard hourly charge) and data volume (per GB).

## NAT Instance

- If you'd like to use an EC2 instance as a NAT instance, you must disable source/destination checks.

## NAT Gateways vs Instance

Are kinda the same. Both need:

- Public IP
- Running in public subnet
- Functional internet gateway

However, it is not really recommended to use a NAT instance. AWS recommends using a NAT gateway for most situations.

NAT Gateway
- Availability
  - HA in AZ, but it will still fail entirely if the AZ fails.
- Bandwidth
- Low maintenance
- High performance
- Not free tier eligible
- Managed service so you cannot use it as a bastion host (cannot connect to its OS).
- Can only use NACLs, don't support SGs.

NAT Instance
- Limited by instance it is running on
- General purpose so not as much customze designed performance
- Is a single EC2 instance running in an AZ and likewise it will fail if storage, networking, hardware, or AZ itself fails entirely.
- For a cost conscious business, it can be cheaper to use a NAT instance or an option if it is very low volume (such as a test VPC). It can also be much cheaper at a high volume of data.
  - Can use a small EC2 instance, even ones that are free tier eligible. The instances can be fixed in size which means you'd have a fixed cost.
- Can connect to them just like any other EC2 instance or use them for multiple purposes.
- Port forwarding
- Can use network ACLs or SGs on the instance.

## IPv6?

- NAT isn't required for IPv6
- All IPv6 addresses in AWS are publicly routable
- Internet Gateway works with ALL IPv6 IPs directly
- NAT gateways don't work with IPv6
- ::/0 route + IGW for bi-directional connectivity
- ::/0 route + Egress-only internet gateway - outbound only
