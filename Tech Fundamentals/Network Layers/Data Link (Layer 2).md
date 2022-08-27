Requires a functional layer 1 to operate. This is common in the OSI model that higher layers need lower layers in order to operate.

L2 provides controlled access to the physical medium.

Devices at L2 all have a unique hardware (MAC) address (48 bits in hex, 3e:22:fb:b9:5b:75). The first 24 bits (OUI, organizational unique identifier) are assigned to companies who manufacture network devices. The second part of the MAC address is network interface controller (NIC) specific. The address should be globally unique. Furthermore, Frames can be addressed to a destination or broadcast.

An Ethernet frame can be transmitted onto the shared physical medium by layer one. It'll be converted into voltages, RF, or light and then sent across to other devices connected on that same shared medium. L2 provides frames. L1 handles physical transmission and reception.

Frame components

* Preamble (56 bits)
  * SFD (8 bits)
* MAC Header
  * Destination MAC Address (or all F's to send to every device on the local network)
  * Source MAC Address (set to the device address of the frame senter)
  * ET (16 bits) (EtherType) - Which layer 3 protocol is putting its data inside a frame (i.e IP)
* Payload (46 - 1500 bytes)
  * Data for the frame.
  * Generally is provided by Layer 3 and the ET attribute will define which L3 protocol is used.
* FCS (32 bits) - Frame check sequence
  * Checks if corruption has occurred or not
