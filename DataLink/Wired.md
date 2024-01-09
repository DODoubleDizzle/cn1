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

## CSMA/CD
Carrier Sense Multiple Access with Collision Detection, is a network protocol that is used on bus and hub network setups.

**Carrier Sense (CS)**
Before a device (like a computer or printer) begins to transmit data over the network, it first checks to see if the channel is free. This means it listens to see if any other device is currently transmitting. If the channel is busy, the device waits.
    
**Multiple Access (MA)**
This part of the protocol indicates that multiple devices are connected to the same network and have the ability to access the network channel to transmit data. Each device has an equal chance to transmit.
    
**Collision Detection (CD)** 
Despite the carrier sensing, sometimes two devices might start transmitting at the same time, leading to a collision of data packets on the network. CSMA/CD can detect this collision. When a collision is detected, each device stops transmitting and waits for a random period before attempting to retransmit. This random wait time helps to reduce the chance of another collision.

**Binary Exponential Backoff**
This is the algorithm used in CSMA/CD. After detecting a collision, each device waits for a random period before trying to retransmit. This period is determined by the algorithm.
    
**Collision Count**
Each device keeps a record of the number of collisions that have occurred for the current frame it's trying to transmit. This count is used in the backoff algorithm calculation.
    
**Random Time Delay**
The device picks a random time delay, which is based on the number of collisions that have occurred for that frame. Specifically, the device chooses a random number of slot times (a slot time is the time it takes for a signal to travel the maximum theoretical length of an Ethernet network and back, which is 51.2 microseconds for traditional Ethernet) from a range of 0 to 2^n−1, where n is the collision count, capped at a maximum value (usually 10). This ensures that the more collisions a frame experiences, the wider the range of random backoff times, helping to reduce the likelihood of repeated collisions.
    
**Waiting Period**
The device then waits for the determined random time delay before trying to transmit again.
    
**Reattempt Transmission**
After the waiting period, the device checks again to see if the line is idle (carrier sense) and attempts to transmit. If another collision occurs, the collision count is incremented, and the process repeats.
    
**Maximum Attempts**
There's a limit on how many times the device will try to retransmit the frame (usually 16 attempts). If this limit is reached, the frame transmission is aborted, and an error is reported.
