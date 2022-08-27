## Considerations

* IP Range (VPC cidr)

* Should know VPC range in advance

* What size should the VPC be?
  
  * Influences how many things/services can fit into the VPC
  * Each one has an IP that occupies space in the VPC
* Are there any networks we can't use?
  
  * Overlapping or duplicate ranges would make network communication difficult
* VPC's, Cloud, On-premises, Partners & Vendors
  
  * Avoid other ranges that other parties you need to interact with may use
* Try to predict the future..

* VPC Structure
  
  * Tiers
  * Resiliency (Availability) Zones
* VPC minimum /28 (16 IP addresses), maximum /16 (65456 IPs)

* Personal preference for the 10.x.y.z range

* Avoid common ranges - avoid future issues
  
  * 10.0
  * 10.1
  * 10.10
  * Start 10.16?
* Reserve 2+ networks per region being used per account
