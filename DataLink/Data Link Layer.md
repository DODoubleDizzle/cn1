# Table of contents
- [[Domains|Domains]]
	- [[Domains#Collision Domain|Collision Domain]]
	- [[Domains#Broadcast Domain|Broadcast Domain]]
- [[Frames|Frames]]
- [[Wired|Wired]]
	- [[Wired#Full Duplex|Full Duplex]]
	- [[Wired#Half Duplex|Half Duplex]]
	- [[Wired#Auto-Negotiation|Auto-Negotiation]]
	- [[Wired#CSMA/CD|CSMA/CD]]
- [[Wireless|Wireless]]
	- [[Wireless#CSMA/CA|CSMA/CA]]
	- [[Wireless#Management Frames|Management Frames]]
	- [[Wireless#Roaming|Roaming]]
		- [[Wireless#Handoff|Handoff]]
- [[Ethernet Addressing|Ethernet Addressing]]
- [[Mac Learning|Mac Learning]]
- [[ARP|ARP]]
- [[Spanning Tree|Spanning Tree]]
- [[VLAN|VLAN]]
- [[Trunking|Trunking]]
- [[Port Aggregation|Port Aggregation]]
	- [[#Hidden Node Problem|Hidden Node Problem]]


# Domains
![[Pasted image 20240103095036.png]]
## Collision Domain
Collision domains are spaces where frames can collide. These happen on directly connected, half duplex devices for example a bus. These domains get split by switches (layer 2) and routers (layer 3) creating a collision domain for each port
## Broadcast Domain
The broadcast domain is a space where a broadcast will reach, switches flood broadcasts through all ports but routers do not, so broadcast domains will be split by routers.
# Frames

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

# Wireless
## CSMA/CA
**Carrier Sense**: Just like in CSMA/CD, the first step in CSMA/CA is for the device to check if the channel is free before it starts transmitting data. This is done by listening to see if any other device is currently transmitting on the same channel.

**Collision Avoidance**: Since it's hard to detect collisions in wireless networks (due to the [[Hidden Node Problem|"hidden node problem"]] where two devices might be out of range of each other but still able to interfere with a common receiver), CSMA/CA tries to avoid collisions before they happen.

**Random Backoff Time**: If the channel is busy, the device waits for a random backoff time before checking the channel again. This backoff time helps in reducing the probability of two or more devices trying to transmit at the same time after the channel becomes free.

**Acknowledgment (ACK)**: After a device sends a frame, it waits for an ACK from the receiving device. If the ACK is not received within a certain timeframe, the sending device assumes that the frame was lost (possibly due to a collision) and retransmits the frame.

**Optional Steps (RTS/CTS)**: In some cases, especially when the data packets are large, CSMA/CA uses a Request-to-Send/Clear-to-Send (RTS/CTS) mechanism. Before sending a large packet, the sending device transmits a short RTS frame to the receiving device, which, if available, replies with a CTS frame. This RTS/CTS exchange informs other devices to avoid transmitting for a certain duration, thus further reducing the chances of collision.


## Management Frames
**Probe Request**
Smartphone sends probe requests containing own capabilities and supported rates uses own smallest supported rates for data rate, type is 0x0004.
![[Pasted image 20240103115418.png]]

**Probe Response**
The access point replies with its own capabilities and sends the frame on the lowest rate also. The Probe Response is 0x0005, country information and environment.
![[Pasted image 20240103115642.png]]

**Authentication Request**
Auth Seq Num: 1
![[Pasted image 20240103134643.png]]

**Authentication Response**
Auth Seq is 0x002
![[Pasted image 20240103132753.png]]

**Deauthentication Frame**
![[Pasted image 20240103135312.png]]

**Association Request**
DS = Distribution System
![[Pasted image 20240103135719.png]]

**Association Response**
![[Pasted image 20240103135551.png]]

**Reassociation Request**
![[Pasted image 20240103135843.png]]

**Reassociation Response**


Dissasociation Frame
![[Pasted image 20240103135919.png]]

**Beacon**
![[Pasted image 20240103135942.png]]

Timing Advertisment

**Request to send**
![[Pasted image 20240103140147.png]]


**Acknowledge Frame**
![[Pasted image 20240103140204.png]]

## Roaming
**Over the Air (OTA)**: This term refers to the wireless part of the roaming process. It involves the actual radio transmission between the mobile device (like a smartphone or laptop) and the access point (AP). When a device roams OTA, it switches its connection from the current AP to a new AP. This involves:
- Scanning for and identifying a new AP with a stronger signal as the device moves.
- Authenticating and associating with the new AP.
- The transition of the wireless communication link from the old AP to the new one.
- This process is critical in maintaining an active network connection as the user moves throughout the coverage area.
**Over the Distribution System (ODS)**: This term is related to the backend infrastructure of a wireless network. The distribution system is essentially the network of devices and connections that interlink various APs. In the context of roaming:
- It involves the transfer of the device's session and context from the old AP to the new AP through the wired network infrastructure.
- This is crucial in enterprise or large-scale Wi-Fi networks where multiple APs are connected to a centralized network controller or switch.
- ODS roaming ensures that as the device moves and changes its point of wireless connection, the network's backend seamlessly maintains the session without interruption or data loss.
### Handoff
When switching from one access point to another because the other one has better signal quality.
![[Pasted image 20240103152031.png]]
# Ethernet Addressing



# Mac Learning
When a frame arrives at a switch, the switch examines the frame's source MAC address and the port it arrived on. If this MAC address is not in the switch's MAC address table, the switch adds it, associating this MAC address with the corresponding port. This process is automatic and dynamic.

# ARP 
1. **Function**: ARP is used for mapping an IP address to a MAC address. When a device wants to communicate with another device on the same network, it needs to know the MAC address corresponding to the target device's IP address.
2. **Process**:
    - The device sends an ARP request, which is a broadcast message on the network, asking "Who has IP address X.X.X.X?"
    - All devices on the network receive this ARP request.
    - The device with the specified IP address responds with an ARP reply, providing its MAC address.
3. **ARP Cache/Table**: Devices maintain an ARP cache (or table) where they store IP-to-MAC address mappings for some time. This cache reduces the need to send ARP requests repeatedly.

# Spanning Tree
STP is a network protocol that ensures a loop-free topology for Ethernet networks. The basic function of STP is to prevent bridge loops and the broadcast radiation that results from them. STP was originally defined in IEEE 802.1D.
1. **Root Bridge Election**: All switches in the network claim to be the root bridge initially. The switch with the lowest bridge ID (a combination of a priority number and the switch's MAC address) becomes the root bridge.
2. **Path Selection**: Each switch determines the shortest path to the root bridge. The port on the switch that provides the shortest path to the root bridge becomes the root port.
3. **Designated and Non-Designated Ports**: For every network segment, there is a designated port (the port opposite to the root port). All other ports are non-designated and are put into a blocking state, effectively disabling them to prevent loops.
4. **Listening State**: The default time for the listening state is 15 seconds. During this period, the switch processes BPDUs (Bridge Protocol Data Units) and determines the network topology without forwarding frames or learning MAC addresses.
5. **Learning State**: The learning state also typically lasts for 15 seconds. In this state, the switch learns MAC addresses but does not forward user frames. The duration is intended to populate the MAC address table before starting to forward frames.
6. **Forwarding State**: Once a port enters the forwarding state, it remains in this state as long as the network topology stays unchanged and no topology changes are detected that would require the port to change state.
7. **Blocking State**: The duration of the blocking state can vary. A port enters the blocking state when STP determines that it could cause a loop if it were active. The port will remain in the blocking state until STP determines that it is safe to move the port to the listening state, potentially leading to a transition to the forwarding state.
8. **Convergence**: Once all the ports on all the switches have been appropriately configured, the network is considered to have converged.

# VLAN
1. **Definition**: A VLAN is a logical subdivision of a local area network (LAN) that groups together a collection of devices from different physical LAN segments. VLANs allow network administrators to partition a single physical network into multiple virtual networks.
2. **Benefits**:
    - **Segmentation**: It improves network performance and traffic management by segregating large networks into smaller, more manageable segments.
    - **Security**: By segmenting the network, VLANs can increase security as devices on one VLAN cannot directly communicate with devices on another VLAN without proper routing.
    - **Flexibility**: VLANs provide the flexibility to group users by function rather than location. For instance, all members of a particular department can be on the same VLAN regardless of their physical locations in the building.

# Trunking
1. **Definition**: VLAN trunking is a method used to transport multiple VLANs over a single network link. Trunking is typically used between switches, and between switches and routers or other network devices that support VLANs.
2. **Operation**:
    - **Trunk Ports**: On a switch, ports configured for trunking can carry traffic for multiple VLANs. These ports are typically connected to other switches or to routers.
    - **Tagging**: VLAN trunking often uses a tagging protocol like IEEE 802.1Q to identify the VLANs on the trunk link. Each frame on the trunk link is tagged with a VLAN identifier (ID) to indicate the VLAN to which it belongs.
    - **Handling Traffic**: When a trunk port receives traffic, it determines the VLAN based on the tag and forwards the traffic only to ports within that VLAN. If a frame is untagged, it is assigned to a default VLAN, typically VLAN 1.

- **Tagged vs. Untagged Ports**: In the context of VLAN trunking, ports on a switch can be either tagged or untagged. Tagged ports understand and use VLAN tags, while untagged ports belong to a single VLAN and do not use VLAN tags.
- **Native VLAN**: The native VLAN is a special VLAN on a trunk port that carries untagged traffic (VLAN ID =0). It's essential for backward compatibility with older devices that don't understand VLAN tags.
# Port Aggregation
Port Aggregation, also known as Link Aggregation, is a method used in computer networking to combine (aggregate) multiple network connections in parallel. This technique increases throughput and provides redundancy in case one of the links fails. 
1. **Purpose**: The primary goal of port aggregation is to increase the network capacity beyond the limits of any single network cable or port. It also enhances the reliability and availability of the network connection.
2. **How it Works**:
    - **Multiple Ports**: It involves combining two or more network connections (usually Ethernet) into a single logical link.
    - **Load Balancing**: The aggregated link can balance the traffic load across the individual links, which can increase the effective bandwidth.
    - **Redundancy**: If one of the physical links in the aggregation fails, traffic can continue to flow over the remaining links, reducing the risk of network downtime.

## Hidden Node Problem

![[Pasted image 20240103111131.png]]


**Scenario Setup**
Imagine a Wi-Fi network with an access point (C) and two devices, Node A and Node B. Node A and Node B are both within range of the AP but are not within range of each other - perhaps they are separated by a wall or are at opposite ends of the AP's range.

**Collision Risk**
If Node A starts sending data to the AP, and Node B cannot detect this transmission (since Node A is "hidden" from Node B), Node B might also start sending data to the AP simultaneously. Since neither node can detect the other's transmission, they both believe the channel is clear and proceed to send their data.

**Resulting Collision**
The AP receives overlapping signals from Nodes A and B, causing a data collision. This leads to garbled and unintelligible information being received by the AP.

**Network Inefficiency**
Both Node A and Node B, upon realizing the collision (often through the lack of acknowledgement from the AP), will have to resend their data after waiting for a random period. This not only slows down the communication but also increases the network's load, leading to inefficiency.

**Solution - RTS/CTS Mechanism**
To mitigate the hidden node problem, protocols like IEEE 802.11 (Wi-Fi) often use the Request to Send/Clear to Send (RTS/CTS) mechanism. Before sending a long frame of data, a node sends a short RTS frame to the AP, indicating its intention to transmit for a specific duration. The AP then responds with a CTS frame, acknowledging the request and informing all other nodes to hold off on their transmissions for that duration. This way, even nodes that can't see each other will be aware of ongoing transmissions, thereby reducing the chances of collision.