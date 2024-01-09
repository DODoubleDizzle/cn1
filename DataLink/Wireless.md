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