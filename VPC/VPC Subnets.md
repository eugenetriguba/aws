* AZ Resilient
* A subnetwork of a VPC - within a particular AZ
* 1 Subnet => 1 AZ, 1 AZ => 0+ Subnets
* IPv4 CIDR is a subset of the VPC CIDR
* Cannot overlap with other subnets
* Optional IPv6 CIDR (/64 subset of the /56 VPC - space for 256)
* Subnets can communicate with other subnets in the VPC

## Subnet IP Addressing

* Reserved IP addresses (5 in total)
* 10.16.16.0/20 (10.16.16.0 => 10.16.31.255)
* Network Address (16.16.16.0)
* 'Network + 1' (10.16.16.1) - VPC Router
* 'Network + 2' (10.16.16.2) - Reserved (DNS\*)
* 'Network + 3' (10.16.16.3) - Reserved Future Use
* Broadcast Address (10.16.31.255) (Last IP in subnet)

Subnet Level configuration options

* DHCP Options Sets
* Auto Assign Public IPv4
* Auto Assign IPv6
