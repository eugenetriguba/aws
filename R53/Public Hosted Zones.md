* R53 Hosted Zone is a DNS DB for a domain
* Globally resilient (multiple DNS servers)
* Created with domain registration via R53 - can also be created separately.
* Monthly fee for each hosted zone and each query made against the hosted zone
* Hosts DNS records (e.g. A, AAAA, MX, NS, TXT)
* Hosted zones are what the DNS system references - Authoritative for a domain
* DNS Database (zone file) hosted by R53 (Public Name Servers)
* Accessible from the public internet & VPCs
* Hosted on "4" R53 Name Servers (NS) specific for the zone
  * Use "NS Records" to point at these NS (connect to global DNS)
* Resource Records (RR) created within the Hosted Zone
* Can be used to host zone files for externally registered domains
* 
