* Regional Service - All AZs in the Region
* Isolated networks
* Nothing allowed IN or OUT without explicit configuration
* Flexible configuration - simple or multi-tier
* Hybrid networking - other cloud & on-premises
* Default or dedicated tenancy!
  * Dedicated tenancy is locked in
* IPv4 Private CIDR Blocks & Public IPs
* 1 Primary Private IPv4 CIDR Block
* Min /28 (16 IP) Max /16 (65,536 IP)
* Optional secondary IPv4 Blocks
* Optional single assigned IPv6 /56 CIDR Block
  * Let AWS assign or use addresses you own
  * Don't have concept of public/private. All public
  * Still have to explicitlly allow IN/OUT

## DNS in a VPC

* Provided by R53
* VPC Base IP + 2 Address
* enableDnsHostnames - gives instances DNS names
* enableDnsSupport - enable DNS Resolution in VPC
