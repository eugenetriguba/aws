A & AAAA

* Given a DNS zone, these type of records map hostnames to IP address.
* Different between A and AAAA is the type of IP address.
  * A www maps to IPv4
  * AAAA www maps to IPv6

Canonical Name (CNAME)

* For a given zone, this record type lets you make the equivalent of DNS shortcuts.
* Host to host records.
* We can have an "A server" record but that server may serve multiple functions so we have CNAMEs for ftp, mail, and www all point to that same A record.
* CNAMEs are for reducing admin overhead.
* CNAMEs can only point at other names, not IP addresses.

MX

* Find a mail server (SMTP) for a domain.
* Two main parts: Priority and a value.
* The value can be just a host
  * MX 10 mail (if in the google.com zone, this means mail.google.com)
  * MX 20 mail.other.domain. (Dot on the right means a fully qualified domain name, can be inside this zone or another zone).
  * Lower values are higher priority.
* With an a record (A mail -> IP), the server will make an MX query in the google.com zone for the domain to use.
* With the MX record, it uses the value to query the A record IP address via SMTP and deliver the mail.

Nameserver (NS)

* Allow delegation to occur in DNS
* Root will have NS records that point at .com and .com will have NS records that point at the amazon.com zone and so on.

TXT

* Allows arbitrary records for a domain.
* Often used to prove domain ownership. Something may say to add a TXT record with a particular value for the domain zone and then once added, query for that TXT record and verify it matches.
* Can be used to fight spam.

TTL (Time to live) values on record

* Numeric value in seconds
* When we lookup a domain, we go through the resolver and go through the recursive lookup process of looking at the root, the TLD, etc. Once we find the record we need, it will have a TTL attached to it. This is known as an authoritative response.
* This value in seconds is how long the resolver should cache.
* When retrieving from the cache, that answer is non-authoritative.
* Normally both of these are the same, so it doesn't matter. TTL matters for when things do change. If you migrate an email service and have a high TTL value, then email delivery may be delayed because old IP addresses are still cached.
* Trade off: low value means more queries but more control over changing that value (less impact). High values mean more queries to the NSs but a higher impact when you need to change.
* If you know you're going to need to make a DNS change, it is often wise to lower that TTL value days or weeks in advance.
