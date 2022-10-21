# Simple Routing

Simple routing lets you configure standard DNS records with no special Route 53 routing such as weighted or latency. With simple routing, you typically route traffic to a single resource, for example, to a web server for your website.

- Simple routing doesn't support health checks
- All values are returned in a random order
- Supports 1 record per name (www)
- Each record can have multiple values

Use simple routing when you want to route requests towards one service such as a web server.
