
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