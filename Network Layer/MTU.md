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
