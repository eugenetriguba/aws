Data Link (Layer 2)

* Send data to a known MAC address by creating a frame (F1). 
* Communicates via Layer 1 but checks the carrier (Carrier Sense Multiple Access) to ensure it can send data without interference.
* If there isn’t a carrier, the frame is sent over Layer 1. Layer 1 doesn’t understand the frame as anything other than a block of data.
* The other device receives the frame, ensures that the destination mac address is for itself, and passes the payload on the device where needed.

Layer 2 adds MAC address to address machine-to-machine communication and the ability to sense when the shared medium is being used to ensure there is no data interference (media access control).

If a collision is detected, a jam signal is sent by all devices that detect it and then a random backoff occurs. The backoff is a period of time that no device attempts to attempt a transmission before re-transmission occurs.

Encapsulation: Taking data and wrapping it in something else. As data is passed down the OSI model, the data is handled through layers of encapsulation.

HUBS are layer ones devices. They don’t understand frames in any way, just see raw data. They are a multiport repeater. This means that collisions are also repeated and impact all devices.

Instead, we can use a switch. A switch works similar to a HUB but it understands layer 2 so it provides significant advantages.

* Understand frames and MAC addresses. Maintains a MAC address table that starts off empty and as the switch receives frames on its ports, it learns which devices are connected to which ports and populates the table.
* Switches are most intelligent since they aren’t just repeating the physical level. If a frame is transmitted to a particular MAC address and that address is in the switch’s table, it will be transmitted directly to it. Otherwise, if it is not in the table, it will be transmitted to all ports. Any frames that have “All f’s” will always be forwarded to all ports.
* Switches store and forward frames. They don’t blindly repeat like hubs.
* Identifiable devices
* Media Access control (sharing access with physical media)
* Collision Detection (correct or work around collisions)
* Unicast 1:1
* Broadcast 1:All
* Switches - like Hubs with super powers (Layer 2)
