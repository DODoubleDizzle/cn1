# NAT
**Translation of Addresses:**
In a typical scenario, multiple devices on a private network (like a home or office network) have their own private IP addresses. When these devices connect to the internet, NAT translates these private IP addresses into a public IP address. The router or NAT device has at least one public IP address.
**Conserving Public IP Addresses:**
Since the IPv4 address space is limited, NAT helps conserve public IP addresses by allowing multiple devices to share a single public IP address.
**Types of NAT:**
- **Static NAT**: A one-to-one mapping between a private IP address and a public IP address. It's often used for devices that need a permanent IP address, like a web server.
- **Dynamic NAT**: Dynamically assigns a public IP address from a pool of available addresses. No two devices have the same public IP at the same time.
![[Pasted image 20240105135943.png]]
### NAT Process
#### Outgoing Packets
When an internal device sends a packet to the internet, the NAT device replaces the source private IP address in the packet header with its own public IP address. It also changes the source port number and keeps a record in a NAT table to remember which internal device the packet came from.
#### Incoming Packets
When the NAT device receives a packet from the internet, it looks at the destination port number, checks its NAT table, and forwards the packet to the corresponding internal device after changing the destination IP address back to the private IP address of that device.