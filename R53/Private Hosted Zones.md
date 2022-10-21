# Private Hosted Zones

A private hosted zone is a container that holds information about how you want Amazon Route 53 to respond to DNS queries for a domain and its subdomains within one or more VPCs that you create with the Amazon VPC service.

- Operates in the same manner as a public hosted zone, just isn't public.
- Associated with VPCs and only accessible in those VPCs.
- Using different accounts is supported via CLI/APIs.
- Split-view (overlapping public & private) for PUBLIC and INTERNAL use with the same zone name. You can have some DNS records that are private and have an overlapping set of public zone ones.
- Inaccessible from the public internet. Zone cannot be queried outside of associated VPCs.
