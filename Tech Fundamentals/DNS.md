Domain name system (DNS): A discovery service

* Translates things a machine needs into what a human needs and vice versa. i.e. URL to IP address
* Because of the number of sites and services on the internet, the database for DNS is massive and distributed.
* 4,294,967,296 IPv4 Addresses.
* Order of magnitudes more IPv6 addresses.

Computers don't work with domain names. They work with IP addresses. The names are resolved to the actual IP addresses we need.

Zone file:

* amazon.com
* www => 104.98.34.131 (DNS record)
* Hosted by nameserver (NS)
* Resolver will query for this zone file and use the result to access the website. It does this in a way that is distributed, resilient, and scalable.

DNS Client => our device (laptop, phone, etc.)
Resolver => software on your device, or a server which queries DNS on your behalf.
Zone => A part of the DNS database
Zonefile => physical database for a zone
Nameserver => where zonefiles are hosted

Find the nameserver for a particular zone that hosts a particular Zonefile and then query that NS for a record that is in that Zonefile.

DNS Root (and Root Zone)

* Starting point for DNS (upside down tree).
* The domains are separated by a period and then the read from right to left. If the domain does not contain a period at the end, the browser will add it. That period at the end is known as the DNS root.
* This DNS root is hosted on 13 special nameservers known as the root servers. Opearted by 12 different large global companies. These organizations however only manage the servers themselves, not the root zone database.
* These aren't really 13 servers since each server can be a cluster of servers distributed globally but it represented by one entity.
* Using a root hints file, the resolver can find the root servers.

Root zone

* Managed by IANA (Internet assigned numbers authority)
* Their job to manage the contents of the root zone (separate from managing the root servers).
* In charge of the DNS system since they control the root zone.

DNS is built on trust. At the start, our laptop will only trust the root zone since it has been told to (either directly by the root hints file or because it has been told a DNS resolver server which itself trusts it because of a root hints file).

When something is trusted, it is known in DNS as an authority and it is authoritative. One part could be authoritative for root, another for amazon.com. At the start, root zone is the only thing that is authoritative.

Root zone is a database of the most top level domains (TLDs, i.e. .com, .org, .gov, etc.).

Management of these TLDs is offloaded to registries. One org. will manage .org, another .com, etc.

DNS: walking the tree. Information is distributed and delegation is done to get you closer to what you need (recursive).

Summary:

* Root hints => config points at the root servers IPs and addresses
* Root Server => hosts the DNS root zone
* Root Zone => points at TLD authoritative servers
* gTLD => generic top level domain (.com, .org)
* ccTLD => country-code top level domain (.uk, .eu, etc.)
