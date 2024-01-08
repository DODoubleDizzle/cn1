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
## ack
## slow start
## congestion avoidance
## duplicate ack
## fast retransmit
## fast recovery
## sliding window
## MSS
## push / urgent
# DHCP
## discover
## offer
## request
## acknowledgement
## relay agent
## helper-address
# DNS
## hierachy
## authoritative
## recursive
## iterative
## ttl
## RRs
# Network management
	FACPS
	Old school protocols