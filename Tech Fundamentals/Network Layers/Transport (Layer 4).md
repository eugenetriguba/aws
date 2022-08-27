## Layer 3 Problems

* Each packet is routed independently (so may arrive out of order)
  * L3 provides no ordering mechanism
* Packets can go missing. Communication is not guaranteed to be reliable and packets can be lost en route (TTL or route hops).
* Per packet route can introduce delays to packets en route. Different packets can experience different delays.
* No communication channels - packets have a source and destination IP but no method of splitting by app or channel.
* No flow control. If the source transmits faster than the destination can receive, it can saturate the destination causing packet loss.

TCP/UDP both run on top of IP and used in same manner. Use IP as transit. TCP has a more reliable connection oriented architecture whereas UDP is all about performance.

## TCP (Transmission Control Protocol)

* Reliability (and slower), Error correction, and ordering of data
* Used by HTTP/HTTPS/SSH/etc.
* Connection oriented (need to setup connection between two devices and then bi directional channel of communication is created).
  * Connection is established between two devices using a random port on a client and a known port on the server.

### Segments

* Segments don't have SRC and DST IP's. The packets provide the device addressing.
* Segments are encapsulated within IP packets.
* Ports enable multiple streams of communication.

#### Header Format

* Source Port
* Destination Port
* Sequence Number
  * Incremented with each segment that is sent
  * Can be used for error correction and packets are correctly ordered.
  * Uniquely identified segment within a particular connection.
* Acknowledgement
  * One side can indicate up to and including a certain sequence number. Every segment needs to be acknowledged.
* Flags 'N' Things (\*)
  * URG
  * ACK
    * Acknowledge
  * PSH
  * RST
  * SYN
    * Sync sequence numbers
  * FIN
    * Close
* Window
  * Defines number of bytes you're willing to receive between acknowledgements
  * Flow control, allows receiver to control the amount of data it receives.
* Checksum
  * Error checking and arranging for re transmission
* Urgent Pointer
  * Latency sensitive 
* Options
* Padding

Then data.

### Three way handshake

1. Client creates segment to send to server. Contains SYN flag and a random sequence number (call 'cs' for this example). This lets the server know the sequence the client intends to start with.
1. The Server responds back with a SYN and ACK. ACK is 'cs' + 1 and SYN is it's own sequence number (call 'ss' for this example).
1. The Client then sends a sequence of 'cs' + 2 and an ACK of 'ss' + 1. This confirms to the Server that the client understands and is okay with the server sequence value.

Now the connection is established and data can be transferred.

### Firewalls

* A stateless firewall would see two things
  
  * Outbound (LAPTOP IP & tcp/...) => (SERVER IP & tcp/443)
  * Response (SERVER IP & tcp/443) => (LAPTOP IP & tcp/...)
  * TWO RULES will be required (OUT and IN)
  * Network ACL (AWS)
* A stateful firewall views sees one thing
  
  * Outbound .. LAPTOP IP & tcp/... => SERVER IP & tcp/443
  * Allowing the outbound implicitly allows the inbound response

## UDP (User Datagram Protocol)

* Faster but less reliable
