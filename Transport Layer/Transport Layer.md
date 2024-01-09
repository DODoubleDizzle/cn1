- [[#3 way handshake|3 way handshake]]
	- [[#3 way handshake#SYN|SYN]]
	- [[#3 way handshake#SYN/ACK|SYN/ACK]]
	- [[#3 way handshake#ACK|ACK]]
- [[#Slow start|Slow start]]
- [[#congestion avoidance|congestion avoidance]]
- [[#duplicate ack|duplicate ack]]
- [[#fast retransmit|fast retransmit]]
- [[#fast recovery|fast recovery]]
- [[#sliding window|sliding window]]
- [[#MSS|MSS]]
- [[#push / urgent|push / urgent]]
- [[#Discover|Discover]]
- [[#Offer|Offer]]
- [[#Request|Request]]
- [[#Acknowledgement|Acknowledgement]]
- [[#Relay agent|Relay agent]]
- [[#Helper-address|Helper-address]]
- [[#Hierarchy|Hierarchy]]
- [[#Authoritative|Authoritative]]
- [[#Recursive|Recursive]]
- [[#Iterative|Iterative]]
- [[#Root|Root]]
- [[#TTL|TTL]]
- [[#RRs|RRs]]
- [[#FACPS|FACPS]]
- [[#Old school protocols|Old school protocols]]

# Port
**Role of Ports in TCP**: A port in TCP is a 16-bit number, which means the range of possible port numbers is from 0 to 65535. Ports are used to identify specific applications or services running on a networked device.
**How Ports Are Used**: When a device sends data over a network, it attaches the destination TCP port number to the data packet. This number tells the receiving device which application or service the packet is intended for. Similarly, the source port number is used to identify the application or service on the sending device.
**Well-Known Ports**: Ports 0 through 1023 are designated as well-known ports and are reserved for specific services. HTTP uses port 80,  HTTPS (HTTP Secure) uses port 443. Services like FTP 21, SSH 22, Telnet 23, SFTP 22.
**Registered Ports**: Ports 1024 to 49151 are known as registered ports, designated for specific purposes by various applications but not as strictly reserved as well-known ports.
**Ephemeral**:  Ports 49152 to 65535 are dynamic or private ports and can be used by any application for temporary connections.
**Socket**: A combination of an IP address and a port number is known as a socket. A socket thus uniquely identifies a specific endpoint of a network connection.

# UDP / TCP Characteristics

|  | **UDP** | **TCP** |
| ---- | ---- | ---- |
| **Connection Type** | Connectionless. It sends data without establishing or maintaining a connection. | Connection-oriented. It establishes a connection before transmitting data and maintains the connection until the communication ends or the connection is terminated (FYN ACK). |
| **Reliability** | Unreliable. There is no guarantee of delivery, order, or error checking. | Reliable. Ensures delivery of data packets in the correct order and retransmits lost packets. |
| **Speed and overhead** | Faster as it has minimal protocol overhead. It does not require a handshake, error recovery, or acknowledgement. | Slower due to the overhead of establishing connections, error checking, and congestion control. |
| **Transmission** | Message-oriented. It treats data as discrete messages called datagrams. | Stream-oriented. It treats data as a continuous stream of bytes. |
| **Header Size** | 8 bytes | 20 bytes minimum |
| **Uses** | Suited for applications where speed and latency is more critical than reliability, such as streaming media (video, audio), online gaming, and DNS queries. | Used for applications where reliability and order are critical, such as web browsing (HTTP/HTTPS), email (SMTP, POP3, IMAP), and file transfers (FTP). |


# TCP
## 3 way handshake
### SYN
**Sequence number:** random
**Ack number:** -
### SYN/ACK
**Sequence number:** [[#SYN]] sequence number
**Ack number:** [[#SYN]] Sequence number + 1
### ACK
**Sequence number:** [[#SYN/ACK]] acknowledge number
**Ack number:**  [[#SYN/ACK]] sequence number + 1

For all following ACK the +1 part gets replaced by the length of the packet because the length of SYN and for FYN is 1

## Slow start
TCP slow start is one of the first steps in the congestion control process. It balances the amount of data a sender can transmit (known as the [[#Congestion Window]]) with the amount of data the receiver can accept (known as the [[#Receiver Window]] ). The lower of the two values becomes the maximum amount of data that the sender is allowed to transmit before receiving an acknowledgment from the receiver.

1. A sender attempts to communicate to a receiver. The sender’s initial packet contains a small congestion window, which is determined based on the sender’s maximum window.
2. The receiver acknowledges the packet and responds with its own window size. If the receiver fails to respond, the sender knows not to continue sending data.
3. After receiving the acknowledgement, the sender increases the next packet’s window size. The window size gradually increases until the receiver can no longer acknowledge each packet, or until either the sender or the receiver’s window limit is reached.

## congestion avoidance
Congestion avoidance works by adjusting the size of the congestion window (the amount of unacknowledged data that can be in transit on the network) based on network conditions
## duplicate ack
A duplicate ACK is sent by the receiver when it receives a packet out of order, indicating that it expects a different sequence number. This can happen if a packet is lost or arrives late. Receiving multiple duplicate ACKs is often a sign of packet loss and is used by the sender to trigger fast retransmission
## fast retransmit
Instead of waiting for a retransmission timer to expire, the sender retransmits the packet after receiving a certain number of duplicate [[ACKs]] for the same data (commonly three).
## fast recovery
Fast recovery is a mechanism to recover from packet loss without closing the congestion window completely. After [[#fast retransmit]] sends the missing packet, fast recovery algorithm reduces the congestion window (but not as much as in a congestion event) and then begins to increase the window size again, but more cautiously.
## sliding window
This is a method used by TCP to control the flow of data packets between the sender and receiver. It ensures that the sender does not overwhelm the receiver by sending more data than it can process. The size of the sliding window varies dynamically based on network conditions and receiver’s capacity.
![[Pasted image 20240108152032.png]]
The green part is also known as usable window.
## MSS
MSS refers to the largest segment of data that the TCP layer can pass down to the IP layer. It does not include the TCP header or the IP header. The MSS is typically negotiated during the connection establishment phase and is used to avoid fragmentation in the IP layer.
## push / urgent
The Push function in [[#TCP]] tells the sender to send all queued data immediately, and the receiver to pass this data to the application upon arrival, without waiting for the buffer to fill up.

The Urgent flag indicates that the segment contains urgent data that should be processed immediately. It's used to send data out-of-band within the same TCP connection.

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

# DNS
## Hierarchy
DNS follows a hierarchical structure. At the top of the hierarchy is the root domain, represented by a dot (.), followed by top-level domains (TLDs) like `.com`, `.net`, `.org`, and country-code TLDs like `.uk`, `.de`. Below these are second-level and further subdomains e.g. `.ost`, `.autoscout24`.
## Authoritative
An authoritative DNS server is one that has the original source data for a domain's Resource Records. It provides responses to queries about domains within its authority, usually hosted by the domain owner. These responses are considered definitive.
## Recursive
A recursive DNS query is one in which a DNS client asks a DNS server to fully resolve a domain name to an IP address. The recursive server will query other DNS servers on behalf of the client, managing the entire DNS query process until it returns the final answer back to the client.
## Iterative
In an iterative query, the DNS client allows the server to return its best answer. If the queried server does not have a match in its DNS cache or zone files, it will return a referral to a DNS server authoritative for a lower level of the domain hierarchy. The client then makes a query to this next server. This process is repeated until an answer is found or all possibilities are exhausted.
## Root
Root servers direct queries to the appropriate top-level domain (TLD) server, like .com, .net, or .org. They are crucial for the functioning of the global DNS system.
There are 13 root server clusters globally, labelled A through M, managed by various organizations and distributed worldwide for redundancy and stability.
## TTL
Time To Live is a value in a DNS record that indicates how long a resolver should cache the DNS query before the information becomes outdated and needs to be discarded. TTL is measured in seconds and the default is 12h (43200 seconds). 
## RRs
Resource Records are entries in a DNS zone file. They provide information about a domain, including its IP address (A record for IPv4, AAAA record for IPv6), mail servers (MX records), name servers (NS records), and other data like CNAME records for domain aliases or TXT records for various texts.

# Network management
## FACPS

## Old school protocols

