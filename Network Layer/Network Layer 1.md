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
9. **Time to Live (TTL) (8 bits):** Decremented by each router the packet passes through. The packet is dropped when TTL reaches zero, preventing it from circulating indefinitely.
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
6. **Hop Limit (8 bits)**: Similar to the TTL field in IPv4, it decrements by one by each node that forwards the packet. The packet is dropped if the hop limit is decremented to zero.
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

# PAT
**Port Address Translation (PAT)/NAT Overload**
Multiple devices on a local network can be mapped to a single public IP address but with a different port number for each session.

# Static Routing
# Dynamic
# Routing
# Dijkstra
# Headers
# TTL
# MTU
# Fragmentation
# ICMP
# ICMPv6
# slaac
# managed flag
# other flag
# solicited node
# routing longest match
# clear ip nat translation
# lunk state routing