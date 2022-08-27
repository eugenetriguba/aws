Virtual Private Cloud (VPC): A virtual network inside of AWS

* Created within 1 account and 1 region
* Regional service (regionally resilient, multiple availability zones)
  * Every VPC is allocated a range of IP addresses (VPC CIDR)
  * Defines the start and end range of addresses the VPC can use.
  * Any incoming communication that is done with that VPC needs to go through the VPC CIDR.
  * Outgoing connections all originate somewhere within that VPC CIDR.
* Private and isolated unless you decide otherwise.
* Two types
  * Default VPC
    * Only 1 max default VPC per region (can be removed and recreated).
    * Only one VPC CIDR and is always the same: 172.31.0.0/16
    * 1 /20 subnet in every availability zone (higher subnet is smaller size).
    * Provided with Internet Gateway (IGW), security group (SG) and NACL.
    * Subnets assign public IPv4 addresses.
    * Preconfigured in a specific way, everything handled by AWS.
    * A lot less flexible than custom VPC.
  * Custom VPCs
    * Many custom VPCs per region.
    * 100% private by default and require everything to be configured end to end in detail. Until configured otherwise, nothing can communicate inside or outside of the private network.
    * Likely use custom VPCs in almost all serious deployments because you can configure them exactly how you need (size, structure, linked to other VPCs, and even communicate to other cloud platforms or on-premises networks)
