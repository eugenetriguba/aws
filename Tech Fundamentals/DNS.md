# DNS

Domain name system (DNS): A discovery service

* Translates things a machine needs into what a human needs and vice versa. i.e. URL to IP address
* Because of the number of sites and services on the internet, the database for DNS is massive and distributed.
* 4,294,967,296 IPv4 Addresses.
* Order of magnitudes more IPv6 addresses.

Computers don't work with domain names. They work with IP addresses. The names are resolved to the actual IP addresses we need.

The job of DNS is to help you locate and get a query response from the authoritative zone which hosts the DNS record(s) you need.

## Why not ONE DNS server?

### Risk

One small group of bad actors could compromise the DNS infrastructure.

### Scaling

Almost everyone who uses the internet uses DNS globally. A server can only get so big.

### Data Volume

Estimates predict there are currently around ~341 million domains and each domain has many records.

Because of the large dataset, parts of the dataset are delegated to certain entities.

## Key Terms

- DNS Zone: a database e.g. \*.netflix.com containing records.

- ZoneFile: The "file" storing the zone on disk.

- Name Server (NS): A DNS server which hosts 1 or more Zones and stores 1 or more ZoneFiles.

- Authoritative: Contains real or genuine records. e.g. one or more NSs may be able to give the real records for \*.netflix.com.

- Non-Authoritative/cached: Copies of records/zones stored elsewhere to speed things up.

## Hierarchical Design

DNS Root 
- Runs on DNS root servers
- Point that every DNS client knows about and trust
- All queries start at the root
- 13 root server IP addreses that host the root zone and the hardware is managed by independent organizations.
- ICANN, NASA, Verisign, and so on hosts one of these.
  - In reality, these IP addresses don't point to one single server.
- Management of the root zone and root servers that host the root zone is different.
- Root zone contains high level information on TLDs, no details.

## Walking the tree

1. Check the local cache and Hosts file
2. Queries Resolver (DNS Resolver, queries for you)
3. Resolver will check it's own local cache
4. If not found, asks Root, for example, www.netflix.com
5. Root zone contains NS records for `.com` Registry NS IPs.
6. Returns .com NS
7. Resolver queries .com TLD NS for www.netflix.com
8. .com TLD delegates to netflix.com NS and gives back the netflix.com NS IPs
9. Returns netflix.com NS
10. Asks netflix.com NS for www.netflix.com
11. Returns DNS record for www.netflix.com IP
12. Resolver caches the result to improve performance for future queries

No one NS has all the answers, but every query gives you the next step. This process, end to end, is called "walking the tree".

## Registering a new domain

- Registrar and hosting provider can be the same or different companies.
-   


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
