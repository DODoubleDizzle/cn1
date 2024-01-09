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

