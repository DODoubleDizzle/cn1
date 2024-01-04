# Wired
## Full Duplex
1gb 
## Half Duplex
## Auto-Negotiation
Auto-negotiation is a process used in Ethernet networks that allows two devices to automatically negotiate the best possible common mode of operation. This includes aspects like speed (10 Mbps, 100 Mbps, 1 Gbps, etc.), duplex mode (half or full duplex), and flow control settings. Auto-negotiation is defined in the **IEEE 802.3ab** standard
**Process**
1. **Advertisement of Capabilities**: 
	When a network device (like a PC or a switch port) is powered on or connected to a network, it uses auto-negotiation to broadcast its capabilities. These capabilities include supported speeds, duplex modes, and other optional capabilities.
2. **Reception and Acknowledgment**: 
	The device on the other end of the link receives this information and compares it with its own capabilities.
3. **Selection of Optimal Settings**: 
	Both devices then automatically choose the highest performance transmission mode that is supported by both. For instance, if one device supports 10,100,1000 Mbps and the other supports only 10,100 Mbps, they will auto-negotiate to use 100 Mbps as the link speed.
4. **Configuration of the Link**: 
	After agreeing on the common settings, both devices configure themselves accordingly. This process is dynamic and can reinitiate if network conditions change (e.g., if a device is replaced or if there is a change in the network infrastructure).

**Speed Mismatch**
A speed mismatch occurs when two linked devices are operating at different speeds, for example, one at 100 Mbps and the other at 1 Gbps.
- Ethernet standards generally don’t support direct speed mismatches. When devices with incompatible speeds are connected, they often fail to establish a link at all.

**Duplex Mismatch**
A duplex mismatch occurs when one device in a two-device link operates in full duplex mode, while the other operates in half duplex. The full duplex side transmits continuously, unaware of the half duplex side’s need to control for collisions. The half duplex side on the other hand perceives the continuous transmission as a collision.
- Frequent collision detection -> cease transmitting and then retry. This can result in significant packet loss and reduced throughput -> observed as slow data transfer speeds, high latency, and increased retransmissions.
