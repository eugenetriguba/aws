Monolithic

* Fails together
* Scales together (high coupled, typically vertically scaled)
* Bills together (always running, always incur charges)

Tiered Architecture

* Each tier can run on different servers
* Tiers are still coupled together
* Tiers can be vertically scaled independently
* Instead of directly connecting to each tier, we can use load balancers.
* Each tier is no longer communicating with a specific tier so that allows us to utilize horizontal scaling.
* However, the tiers are still coupled since each tier expects and requires the others to respond.
* Each tier has to be running something for the app to function.

Evolving with Queues

* Queue: System that accepts messages (can be received or polled from the queue, usually FIFO)
* Upload tier uploads to S3 bucket and then adds a message to queue for processing.
* Auto scaling group at other end (min 0, desired 0, max 1337) based on queue length
* Can then scale from 0 to infinity\* based on load

Microservice Architecture

* Process service, upload service, and store and manage service.
* Upload = producer, process = consumer, store and manager= both

Event-driven architecture

* Event producer
* Event consumer
* Event router
* Event bus
* No constant running or waiting for things
* Producers generate events when something happens
* ..clicks, errors, criteria met, uploads, actions
* Events are delivered to consumers (using event router)
* ..actions are taken & the system returns to waiting
* Mature event-driven architecture only consumes resources while handling events (serverless)
