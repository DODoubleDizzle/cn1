# Routing longest match
Routing longest match is used in the routing forwarding table of a router to determine where to forward the packet to. 
192.16.0.0/14 -> 1100 0000 0001 0000
192.20.0.0/14 -> 1100 0000 0001 0100
![[Pasted image 20240108143504.png]]
Subnet mask is the green line, so 255.248.0.0
The address will result by taking all the 1s on the left side of the subnet mask line.
