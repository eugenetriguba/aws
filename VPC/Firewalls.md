# Stateful vs Stateless Firewalls

## Stateless

- It doesn't understand the state of connections. It sees the request and response part of a connection as two individual parts. Therefore, you have to think about allowing and denying them as two individual rules (1 Inbound, 1 Outbound).

- With clients for a server, the inbound requests will typically come from the client and the outbound response will come from the server. However, there will be other situations, for instance with software updates, where the server will act as the client and make requests to another server.

- 2 rules per connection. Inbound rules can be for request or response, same for outbound. It depends on the perspective.

- Request portion will always be to a well-known port (i.e. 443 for https). The response will be to an ephemeral port. Because the firewall is stateless, it will typically have to allow the full range of destination ports, and this is where stateful firewalls are an improvement.

## Stateful

- Intelligent enough to identify the request and response components of a single request.

- Therefore generally, you typically only have to allow the request and the response will be allowed or not automatically. 

- This significantly reduces the admin overhead and change for mistakes. Furthermore, you don't have to allow the full emphemeral port range because the firewall is smart enough to identify which port is being used and implicitly allow it based on it being the response to a request that you allow.
