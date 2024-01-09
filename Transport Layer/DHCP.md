# DHCP
## Discover
Client broadcasts UDP DHCP Discover message.
## Offer
DHCP server sends a DHCP Offer message to the client. This message contains an IP address that the server is offering to the client, along with other configuration information like subnet mask, default gateway, and DNS server addresses.
## Request
This message is sent to either accept an offer from one DHCP server (and inform the others that the offer is declined) or to renew or rebind an existing IP address lease. 
![[Pasted image 20240108154803.png]]
## Acknowledgement
Upon receiving the DHCP Request message, the chosen DHCP server sends a DHCP Acknowledgement (ACK) message to the client. This message confirms the lease of the IP address to the client for a specific duration and includes other configuration settings.
![[Pasted image 20240108154852.png]]
## Relay agent
A DHCP relay agent is a network device that forwards DHCP packets between clients and servers. Relay agents are used when the DHCP server is not on the same local network as the client. The relay agent forwards requests and replies between the server and the client.

## Helper-address
The `helper-address` is a configuration command used on routers or switches to specify the address of the DHCP server (or relay agent) to which DHCP messages from clients should be forwarded. This command is used when the DHCP server is not located on the same subnet as the clients.
