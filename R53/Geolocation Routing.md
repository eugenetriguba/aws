# Geolocation Routing

Geolocation routing lets you choose the resources that serve your traffic based on the geographic location of your users, meaning the location that dns queries originate from.

It is similar to latency routing. However, the location of customers and resources are used for resolution decisions. Records are tagged with a location (generally ISO standard country codes, ISO contintent codes, 'default', or a subdivision, such as a state in the U.S.).

An IP check verifies the location of the user (normally the resolver).

:warning: Geolocation doesn't return the _closest_ record, it only returns the _relevant (location)_ records (or the set default/no answer).

R53 checks for records
1. In the state (if user is based in the US)
2. The country
3. The continent
4. (optionally) default if none of the above match - it returns the most specific record or "NO ANSWER" if there is no default.

If these match, those records are returned and the process stops.

Use Cases
- Ideal for restricting content based on location, language-specific content, or load balancing across regional endpoints.

**This routing policy type is not about the closest record. It returns relevant records only. You won't get a Canadian record if you're based in the U.K. and no closer records exists.**

Record Types
- Subdivision (U.S. State)
- Country
- Continent
- Default
