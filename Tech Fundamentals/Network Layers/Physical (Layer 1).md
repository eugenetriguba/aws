Mediums can be copper (electrical), Fibre (light), or WIFI (RF).
These mediums all need to be able to carry unstructured information.

Layer 1 specifications define the transmission and reception of **raw bit streams** between a device and a **shared** physical medium. It defines things like voltage levels, timing, rates, distances, modulation, and connectors.

With copper, a binary 1 may be defined as +1 volt and a binary 0 may be defined as a -1 volt. As long as the two devices agree, this data can be transmitted.

At layer 1, there is no device addressing. All data is processed by all devices. If we have multiple devices connected to a hub, anything that is received on any port will then be transmitted on every other port (including errors or collisions).

If multiple devices attempt to transmit at the same time, a collision occurs and likely lead to data corruption.

L1 has no media access control, uniquely identified devices (no device to device communication), or any way of detecting collisions. It doesn't have anything other than defining the standards that all of the devices will use to transmit onto the shared medium and receive from the shared medium.

The more devices are added to a L1 network, the higher the chance of collisions and data corruption. They do not scale well. For it to be useful, we need to add layer 2.
