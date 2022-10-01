# Horizontal vs Vertical Scaling

Scaling: Grow or shrink resources based on system load

## Vertical Scaling

- Each resize requires a reboot - disruption.

- Larger instances often carry a price premium.

- There is an upper cap on performance, the instance size.

- No application modification required. It's simple.

- Works for ALL applications - even monoliths.

## Horizontal Scaling

- Smaller servers are behind a load balancer which distribute the load across servers.

- Sessions, sessions, sessions.
	- Sessions of the user are generally stored on a particular server but with horizontal scaling, this won't work. Throughout interacting with the app, you may interacting with different servers and therefore, different sessions.
	- Requires application support (thought and design) OR off-host sessions

- No disruption when scaling

- Often less expensive, no large instance premium.

- More granular in how you scale

- No real limit on the amount you scale
