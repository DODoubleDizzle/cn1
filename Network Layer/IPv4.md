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
