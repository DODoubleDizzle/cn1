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