Route53

* Register domains
* Host zone files on managed nameservers
* Global service with a single database
* Distributed globally as a single set and replicated between regions (globally resilience).

Register domains

* Relationships with all major domain registries
* Route53 checks with registry if domain is available. If so, it then creates a zone file for the domain being registered (a database with all DNS info for a particular domain). Then it allocates NS for the zone (that it creates and manages, generally has 4 per zone). It puts the file on the 4 managed NS. So when the look up for the domain happens for the .org registry, the lookup will retrieve back the 4 NS that have our zonefile.

Hosted Zones

* Zone files in AWS
* Hosted on four managed name servers
* Can be public
* Or private (linked to VPC(s))
* Stores records (recordsets)
* 
