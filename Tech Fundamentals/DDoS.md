# Distributed Denial of Service (DDoS) Attacks

- Attacks designed to overload websites
- Generate traffic that competes against 'legitimate connections'
- Distributed - hard to block individual IPs/Ranges (cannot be combatted with normal network protections)

Often involve large armies of compromised machines (botnets, hosts that are infected with malware).

## Application Layer - HTTP Flood

Take advantage of the imbalance of processing between client and server. It's easy to request a webpage but often much more complex for the server to give back the webpage.

## Protocol Attack - SYN Flood

Takes advantage of the connection based nature of requests. Normally, a connection is initiated via a three part handshake. SYN Floods spoof a source IP address and initiate a connection attempt of the server but can't contact the source address. So the server hangs there for a specified duration and consumes network resources.

## Volumetric Attacks - DNS Amplification

Relies on the fact that certian protocols, such as DNS, only take small amounts of data to make the request (such as a DNS resolution request) but in response can deliver a large amount of data.

