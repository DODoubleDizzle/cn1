# SLAAC
## Description
Stateless Address Autoconfiguration (SLAAC) is the method for a host to generate their own IPv6 address using a prefix gained from a router advertisement (as a response to a new device being detected in the network) and [[#EUI64|EUI64]] and to check whether it is already in use using [[#Duplicate Address Detection (DAD) |Duplicate Address Detection]]. 

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
