# Fragmentation
## Fragmentation in IPv4:
**Where it Occurs**: In IPv4, fragmentation can occur at both the originating host and at intermediate routers along the packet's path.
**Process**:
- If a packet is larger than the MTU of the next hop, a router can fragment the packet into smaller units.
- Each fragment is then sent as a separate packet. These packets have headers that allow the destination host to reassemble them back into the original packet.
**Identification**: Fragmented packets are identified by specific fields in the IPv4 header, including the [[#IPv4#Header|Fragment Offset]], [[#IPv4#Header|More Fragments flag]], and an [[#IPv4#Header|Identification field]] that helps in reassembling the packets correctly.

![[Pasted image 20240105161305.png]]
## Fragmentation in IPv6:
**Where it Occurs**: In IPv6, fragmentation is handled differently. It is performed only by the source host, not by routers along the packet’s path.
**Process**:
- If a packet is larger than the MTU of the path to the destination, the source host must perform fragmentation before sending the packet.
- IPv6 uses an Extension Header (Fragment Header) to handle fragmentation. The fragmented packets are then sent to the destination, where they are reassembled.
