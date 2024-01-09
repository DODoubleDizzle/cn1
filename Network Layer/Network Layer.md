- [[IPv4|IPv4]]
	- [[IPv4#Header|Header]]
	- [[IPv4#Ranges|Ranges]]
- [[IPv6|IPv6]]
	- [[IPv6#Header|Header]]
	- [[IPv6#Extension headers|Extension headers]]
- [[#RFC1918|RFC1918]]
- [[Subnetting|Subnetting]]
	- [[Subnetting#Classful|Classful]]
	- [[Subnetting#Classless / CIDR|Classless / CIDR]]
- [[NAT|NAT]]
	- [[NAT#NAT Process|NAT Process]]
- [[PAT|PAT]]
- [[Static Routing|Static Routing]]
	- [[Static Routing#How it Works:|How it Works:]]
	- [[Static Routing#Use Cases:|Use Cases:]]
	- [[Static Routing#Advantages of Static Routing:|Advantages of Static Routing:]]
	- [[Static Routing#Disadvantages of Static Routing:|Disadvantages of Static Routing:]]
- [[Dynamic Routing|Dynamic Routing]]
	- [[Dynamic Routing#How it works:|How it works:]]
	- [[Dynamic Routing#Advantages of Dynamic Routing:|Advantages of Dynamic Routing:]]
	- [[Dynamic Routing#Disadvantages of Dynamic Routing:|Disadvantages of Dynamic Routing:]]
- [[Dijkstra|Dijkstra]]
- [[MTU|MTU]]
	- [[MTU#MTU Discovery|MTU Discovery]]
		- [[MTU#IPv4|IPv4]]
		- [[MTU#IPv6|IPv6]]
- [[Fragmentation|Fragmentation]]
	- [[Fragmentation#Fragmentation in IPv4:|Fragmentation in IPv4:]]
	- [[Fragmentation#Fragmentation in IPv6:|Fragmentation in IPv6:]]
- [[ICMP|ICMP]]
	- [[ICMP#Key Functions of ICMP:|Key Functions of ICMP:]]
	- [[ICMP#ICMP Message Types:|ICMP Message Types:]]
	- [[ICMP#Characteristics:|Characteristics:]]
- [[ICMPv6|ICMPv6]]
	- [[ICMPv6#Key Functions of ICMPv6:|Key Functions of ICMPv6:]]
	- [[ICMPv6#ICMPv6 Message Types:|ICMPv6 Message Types:]]
	- [[ICMPv6#Characteristics:|Characteristics:]]
- [[SLAAC|SLAAC]]
	- [[SLAAC#managed flag|managed flag]]
	- [[SLAAC#other flag|other flag]]
- [[solicited node|solicited node]]
- [[routing longest match|routing longest match]]
- [[#clear ip nat translation|clear ip nat translation]]
- [[#link state routing|link state routing]]

# IPv4

## Header
![[Pasted image 20240105104455.png]]

1. **Version (4 bits):** Indicates the version of the IP protocol. For IPv4, this is always set to 4.
2. **IHL (Internet Header Length) (4 bits):** Specifies the header length, the minimum is 20bytes = value 5 with a 4 byte increment.
3. **DSCP (Differentiated Services Code Point) (6 bits):** Used for quality of service (QoS) control, determining the priority of each packet.
5. **Packet Length (16 bits):** Defines the entire packet size in bytes, including header and data.
6. **Identification (16 bits):** Used for uniquely identifying groups of fragments of a single IP datagram.
7. **Flags (3 bits):** Consists of bit fields controlling fragmentation. These include the More Fragments flag and the Don't Fragment flag.
8. **Fragment Offset (13 bits):** Used in packet fragmentation and reassembly. For example, the first fragment has an offset of 0, as it starts at the beginning of the payload. If the first fragment contains 400 bytes of data (excluding the header), the offset for the next fragment would be 50 (as 400 bytes / 8 bytes per unit = 50 units).
9. **Time to Live (TTL) (8 bits):** Decremented by each router the packet passes through. The packet is dropped when TTL reaches zero, preventing it from circulating indefinitely. And a message is returned.
10. **Protocol (8 bits):** Indicates the higher-layer protocol used in the data portion of the IP datagram (e.g., TCP, UDP).
11. **Header Checksum (16 bits):** Used for error-checking the header. It's recalculated at each router, as the TTL changes.
12. **Source IP Address (32 bits):** The IP address of the originating host.
13. **Destination IP Address (32 bits):** The IP address of the destination host.
14. **Options (variable):** Allows for additional options such as timestamps, security, record route, etc. Not commonly used.
15. **Padding (variable):** Ensures the header is a multiple of 32 bits in length.

## Ranges
|  | Public IP Range | Private IP Range | Subnet Mask | # of Networks | # of Hosts per Network |
| ---- | ---- | ---- | ---- | ---- | ---- |
| Class A | 1.0.0.0 to<br>127.0.0.0 | 10.0.0.0 to<br>10.255.255.255 | 255.0.0.0 	 | 126 | 16'777'214 |
| Loopback |  | 127.0.0.0 to 127.255.255.255 | 255.0.0.0 | - | - |
| Class B | 128.0.0.0 to<br>191.255.0.0 | 172.16.0.0 to<br>172.31.255.255 | 255.255.0.0	 | 16'382	 | 65'534 |
| Class C | 192.0.0.0 to<br>223.255.255.0 | 192.168.0.0 to<br>192.168.255.255 | 255.255.255.0 	 | 2'097'150 | 254 |

# IPv6
## Header
![[Pasted image 20240105113107.png]]

1. **Version (4 bits)**: Indicates the version of IP used, which is 6 (0101) for IPv6.
2. **Traffic Class (8 bits)**: Similar to the Type of Service in IPv4, this field is used to differentiate packets and specify the Quality of Service (QoS).
3. **Flow Label (20 bits)**: To maintain the sequential flow of multiple packets going to the same destination. Used to reorder packets.
4. **Payload Length (16 bits)**: Specifies the length of the payload data, in octets, including any extension headers. The length is limited to 65,535 bytes.
5. **Next Header (8 bits)**: Identifies the type of header immediately following the IPv6 header and located at the start of the payload. This field is used to indicate extension headers.
6. **Hop Limit (8 bits)**: Similar to the TTL field in IPv4, it decrements by one by each node that forwards the packet. The packet is dropped if the hop limit is decremented to zero. And a hop limit exceeded message is sent.
7. **Source Address (128 bits)**: The IPv6 address of the sending node.
8. **Destination Address (128 bits)**: The IPv6 address of the destination node.

## Extension headers
![[Pasted image 20240105114056.png]]
![[Pasted image 20240105114119.png]]
# RFC1918
[[#Ranges|The private ranges of ipv4]]

# Subnetting
## Classful 
Is superseded by Classless and CIDR subnetting.
Works by splitting a network into equally large subnets. either /8 /16 or /24
Example:
We have a network 172.16.0.0 with the subnet mask 255.255.0.0
And the following Subnets we need to create for a certain amount of hosts
- Switzerland 1000
- Iceland 340
- Norway 70
- Finland 40
- Sweden 3
For example 172.16.0.0  we would use class c (/24) but then we only have space for 256 hosts meaning it wont work :)

## Classless / CIDR
With Classless Inter-Domain Routing (CIDR), you're not restricted by class boundaries and can use a variable-length subnet mask (VLSM).

| Subnet ID   | Subnet Address  |  Network ID  |     Host Address Range      | Broadcast Address |
| ----------- |:---------------:|:------------:|:---------------------------:|:-----------------:|
| Switzerland |  172.16.0.0/22  |  172.16.0.0  |  172.16.0.1 - 172.16.3.254  |   172.16.3.255    |
| Iceland     |  172.16.4.0/23  |  172.16.4.0  |  172.16.4.1 - 172.16.5.254  |   172.16.5.255    |
| Norway      |  172.16.6.0/25  |  172.16.6.0  |  172.16.6.1 - 172.16.6.126  |   172.16.6.127    |
| Finland     | 172.16.6.128/26 | 172.16.6.128 | 172.16.6.129 - 172.16.6.190 |   172.16.6.191    |
| Sweden      | 172.16.6.192/29 | 172.16.6.192 | 172.16.6.193 - 172.16.6.199 |   172.16.6.200    |
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
# PAT
**Port Address Translation (PAT)/NAT Overload**
Multiple devices on a local network can be mapped to a single public IP address but with a different port number for each session.
# Static Routing
## How it Works:
Static routing has two key components:
**Routing Table**: The network administrator manually enters routes into the routing table. Each route typically includes the destination network, the subnet mask, and the next-hop address or exit interface.
**Data Forwarding**: When a router receives a packet, it checks its routing table to determine where to forward the packet. The router looks for a network address in the routing table that matches the destination address of the packet and forwards the packet accordingly. If there is no default gateway the packet is dropped and an error is returned.

## Use Cases:
**Small Networks**: Ideal for small networks where the network topology is simple and does not change frequently.
**Single Path**: When there is only one path to a destination, static routing can be an efficient choice.
**Controlled Environments**: In environments where network security and the predictability of the routing path are crucial, static routing offers a controlled way to manage traffic.

## Advantages of Static Routing:
- **Simplicity**: Easier to understand and manage in smaller networks.
- **No fluctuating routes**
- **Security**: Since routes are not advertised, it offers a degree of security.
- **Resource Efficiency**: Less CPU and bandwidth usage.

## Disadvantages of Static Routing:
- **Scalability Issues**: Not suitable for large or rapidly changing networks due to the administrative overhead of manual configuration.
- **Lack of Fault Tolerance**: Static routes do not automatically adjust to network changes or failures.
- **Administrative Overhead**: Requires manual intervention to update routes when network changes occur.

# Dynamic Routing
## How it works:
**Routing Protocols**: Routers use dynamic routing protocols like [[Dijkstra]], RIP (Routing Information Protocol), OSPF (Open Shortest Path First), EIGRP (Enhanced Interior Gateway Routing Protocol), or BGP (Border Gateway Protocol) to exchange routing information.
**Routing Information Exchange**: Routers send out messages to neighbouring routers, informing them of their routing tables or changes in the network topology.
**Routing Table Updates**: Each router uses this information to update its routing table, choosing the best paths based on the protocol's algorithm (e.g., shortest path, least cost, fastest speed).
**Adaptation to Changes**: If there's a change in the network, such as a link failure, routers automatically recalculate routes and update their tables accordingly.
## Advantages of Dynamic Routing:
**Flexibility**: Automatically adapts to network changes, reducing the need for manual reconfiguration.
**Fault Tolerance**: Can quickly converge to a new path if a link or router fails.
**Load Balancing**: Some routing protocols can balance traffic load across multiple links to optimize network performance.
## Disadvantages of Dynamic Routing:
**Complexity**: Configuration and management can be more complex compared to static routing.**Resource Usage**: Consumes more CPU, memory, and network bandwidth due to constant exchange of routing information.
**Convergence Time**: In some cases, particularly with larger networks or less sophisticated protocols, it can take time for the network to converge (reach a stable state) after a change.

# Dijkstra
![[Pasted image 20240105155438.png]]


# MTU
The Maximum Transmission Unit (MTU) refers to the size of the largest protocol data unit (PDU) that can be transmitted over a network. MTU is measured in bytes.
## MTU Discovery
MTU discovery is the process of determining the maximum MTU size that can be used for communication between two IP hosts, ensuring that IP packets are transmitted without fragmentation.
### IPv4
**Process**: IPv4 uses a process called Path MTU Discovery to find the smallest MTU along the path from the source to the destination. It starts by sending packets with the Don't Fragment (DF) bit set to the largest possible size. If any of the packets are too large to be forwarded without fragmentation by any router along the path, that router drops the packet and returns an ICMP "Fragmentation Needed and DF set" message to the sender. The sender then reduces the packet to the size in the response and tries again.
### IPv6
**Mandatory Handling of Larger MTU**: Unlike IPv4, IPv6 requires that all links in the internet must handle packets of up to 1280 bytes without requiring fragmentation.
**Process**: IPv6 also uses Path MTU Discovery, similar to IPv4, by initially assuming the MTU of the destination is the MTU of the first-hop link and then discovering the actual path MTU similarly to IPv4. However, because IPv6 does not allow fragmentation at routers, the path MTU discovery process is essential for efficient operation.
**ICMPv6 "Packet Too Big" Message**: In IPv6, if a router encounters a packet larger than the MTU of the next hop, it discards the packet and sends an ICMPv6 "Packet Too Big" message back to the source, indicating the MTU of that next-hop link. The source then reduces its assumed Path MTU to this value and retransmits the packet.

# Fragmentation
## Fragmentation in IPv4:
**Where it Occurs**: In IPv4, fragmentation can occur at both the originating host and at intermediate routers along the packet's path.
**Process**:
- If a packet is larger than the MTU of the next hop, a router can fragment the packet into smaller units.
- Each fragment is then sent as a separate packet. These packets have headers that allow the destination host to reassemble them back into the original packet.
**Identification**: Fragmented packets are identified by specific fields in the IPv4 header, including the [[IPv4#Header|Fragment Offset]], [[IPv4#Header|More Fragments flag]], and an [[IPv4#Header|Identification field]] that helps in reassembling the packets correctly.

![[Pasted image 20240105161305.png]]
## Fragmentation in IPv6:
**Where it Occurs**: In IPv6, fragmentation is handled differently. It is performed only by the source host, not by routers along the packet’s path.
**Process**:
- If a packet is larger than the MTU of the path to the destination, the source host must perform fragmentation before sending the packet.
- IPv6 uses an Extension Header (Fragment Header) to handle fragmentation. The fragmented packets are then sent to the destination, where they are reassembled.

# ICMP
ICMP, or Internet Control Message Protocol, is an integral part of the Internet Protocol Suite, defined by RFC 792 for IPv4. It is used by network devices to send error messages and operational information indicating success or failure in data communication.
## Key Functions of ICMP:
- **Error Reporting**: ICMP reports errors in processing IP packets. This is crucial since the IP protocol itself does not have a built-in mechanism for reporting errors.
- **Diagnostic Tools**: ICMP is used by diagnostic tools such as `ping` and `traceroute`. `ping` uses ICMP Echo Request and Echo Reply messages to check whether a destination is reachable and to measure round-trip time. `traceroute` uses ICMP Time Exceeded messages to determine the path packets take to their destination.
- **Network Testing and Troubleshooting**: Network administrators use ICMP for testing and managing network issues.
## ICMP Message Types:
- **Destination Unreachable (Type 3)**: Indicates that the destination is unreachable for various reasons like network failure, host failure, protocol unreachability, etc.
- **Time Exceeded (Type 11)**: Indicates that the Time-To-Live (TTL) field of an IP packet has reached zero, preventing an infinite loop.
- **Echo Request and Echo Reply (Type 8 and 0)**: Used by the `ping` command to test reachability.
- **Parameter Problem (Type 12)**: Indicates that there is a problem with the packet's header fields.
- **Source Quench (Deprecated)**: Historically used to notify the sender that its packets are being discarded due to congestion at a router.
- **Redirect Message (Type 5)**: Used by routers to indicate a better route for the host.
## Characteristics:
- **Not Used for Data Transfer**: ICMP is not used to transfer application data between devices.
- **Support for Network Operations**: It supports the operation and management of IP networks.
- **Unreliability**: ICMP messages do not guarantee delivery as they don't have error-checking for their own messages. They are not retransmitted if lost.
- **Security Concerns**: ICMP can be used for malicious purposes, such as in Denial of Service (DoS) attacks or ICMP flooding. Therefore, it's sometimes limited or controlled in network environments.

# ICMPv6
## Key Functions of ICMPv6:
- **Error Reporting**: Like ICMP in IPv4, ICMPv6 reports errors encountered in processing IPv6 packets, such as packet delivery issues.
- **Diagnostic Tools**: ICMPv6 is used by tools like `ping` (for Echo Request and Echo Reply messages) and `traceroute` (using Time Exceeded messages) to diagnose network connectivity.
- **Neighbour Discovery Protocol (NDP)**: One of the significant additions in ICMPv6 is its role in the Neighbour Discovery Protocol, which replaces ARP (Address Resolution Protocol) used in IPv4. NDP uses several ICMPv6 message types to manage the interaction of neighbouring nodes, such as Router Solicitation, Router Advertisement, Neighbour Solicitation, Neighbour Advertisement, and Redirect.
- **Path MTU Discovery**: ICMPv6 assists in Path MTU Discovery by sending Packet Too Big messages, helping to determine the optimal packet size for transmission.
## ICMPv6 Message Types:
- **Destination Unreachable (Type 1)**: Informs the sender that a packet could not be delivered to its destination for various reasons.
- **Packet Too Big (Type 2)**: Indicates that a packet cannot be forwarded because it exceeds the MTU of the next-hop link, crucial for path MTU discovery.
- **Time Exceeded (Type 3)**: Similar to IPv4, used for packets that exceed their hop limit (equivalent to TTL in IPv4) or for reassembly timeout.
- **Parameter Problem (Type 4)**: Reports problems with packet headers, such as incorrect or unrecognized field values.
- **Echo Request and Echo Reply (Type 128 and 129)**: Used for the `ping` command, similar to their IPv4 counterparts.
- **NDP Messages**: Including Router Solicitation (Type 133), Router Advertisement (Type 134), Neighbour Solicitation (Type 135), Neighbour Advertisement (Type 136), and Redirect (Type 137).
## Characteristics:
- **Integral to IPv6**: ICMPv6 is more integrated into IPv6 than ICMP is with IPv4, particularly due to its role in NDP.
- **Enhanced Functionality**: Provides important functions for the discovery and maintenance of network connections in IPv6.
- **Security Considerations**: ICMPv6, like ICMP in IPv4, can be a vector for certain network attacks. Proper firewall and security settings are essential to manage and mitigate potential risks.

# SLAAC
## Description
Stateless Address Autoconfiguration (SLAAC) is the method for a host to generate their own IPv6 address using a prefix gained from a router advertisement (as a response to a new device being detected in the network) and [[SLAAC#EUI64|EUI64]] and to check whether it is already in use using [[#Duplicate Address Detection (DAD) |Duplicate Address Detection]]. 

## Duplicate Address Detection (DAD)
Before finalizing its address, the device performs DAD by sending a Neighbor Solicitation message to check if the address is already in use on the local network. If there’s no response, the address is assumed to be unique, and the device configures it on its interface.
## EUI64
EUI64 is a method to create an IPv6 address out of a mac address. It is done by splitting the mac address in the middle and inserting FFFE.
![[Pasted image 20240108112239.png]]
Afterwards you flip the 7th bit, meaning 00010010 (12) becomes 00010000 (10) so the final address becomes:
103456FFFE78ABCD

## Temporary Addresses
The EUI64 part of the IPv6 address gets randomized with a use time of 1 day, after which it will be renewed. On most operating systems this address gets saved for an additional 6 days after, for a total of 7 days.

## Managed flag
M flag stands for Managed Address Configuration and it says to host receiving the RA advertisement that somewhere in his network there is a DHCPv6 server available and that he should send a DHCPv6 request out of his interface to get his IPv6 address. If it is set to 0 the host will not try to get his address from DHCPv6 server but will autoconfigure himself with SLAAC.

## Other flag
Other flag stands for Other configuration and it tells host receiving the RA message that he should use DHCP to get other configuration parts like DNS server IPv6 address. SLAAC in today’s implementation is not able to send the info to the host about DNS server IPv6 address. That will probably force you to use both SLAAC and DHCPv6 to on those subsets where you want to use automatic host configuration method.

# Solicited Node
A "Solicited Node" in IPv6 networking refers to a special type of multicast address that is used for efficient network traffic management, particularly for the Neighbour Discovery Protocol (NDP). 

**Calculation**: A Solicited Node multicast address is automatically generated for each IPv6 address assigned to a network interface. It is formed by combining the prefix `FF02::1:FF` with the last 24 bits (6 digits) of the corresponding IPv6 address. For instance, if a device has the IPv6 address `2001:db8::567:89ab`, the Solicited Node multicast address would be `FF02::1:FF67:89AB`.
**How It Works**: When an IPv6-enabled device needs to learn the MAC address of another device on the same network (for sending packets to it, for example), it sends a Neighbour Solicitation message to the Solicited Node multicast address corresponding to the target device's IPv6 address. This message asks the owner of that IPv6 address to respond with its link-layer address.
**Efficiency**: In IPv4, a similar process (ARP) broadcasts a request to all nodes on the local network, which can lead to inefficiencies, especially in large networks. IPv6 improves upon this by using Solicited Node addresses, which are a type of multicast address listened to only by specific nodes. This results in significantly less local network traffic.
**Scope**: Solicited Node multicast addresses have a link-local scope, meaning they are only relevant and used within the local network segment.
# Routing longest match
Routing longest match is used in the routing forwarding table of a router to determine where to forward the packet to. 
192.16.0.0/14 -> 1100 0000 0001 0000
192.20.0.0/14 -> 1100 0000 0001 0100
![[Pasted image 20240108143504.png]]
Subnet mask is the green line, so 255.248.0.0
The address will result by taking all the 1s on the left side of the subnet mask line.

# clear ip nat translation
`clear ip nat translation` is a command used in Cisco devices to clear all dynamic entries from the NAT table.

# link state routing
## IS-IS
