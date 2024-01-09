# UDP / TCP Characteristics

|  | **UDP** | **TCP** |
| ---- | ---- | ---- |
| **Connection Type** | Connectionless. It sends data without establishing or maintaining a connection. | Connection-oriented. It establishes a connection before transmitting data and maintains the connection until the communication ends or the connection is terminated (FYN ACK). |
| **Reliability** | Unreliable. There is no guarantee of delivery, order, or error checking. | Reliable. Ensures delivery of data packets in the correct order and retransmits lost packets. |
| **Speed and overhead** | Faster as it has minimal protocol overhead. It does not require a handshake, error recovery, or acknowledgement. | Slower due to the overhead of establishing connections, error checking, and congestion control. |
| **Transmission** | Message-oriented. It treats data as discrete messages called datagrams. | Stream-oriented. It treats data as a continuous stream of bytes. |
| **Header Size** | 8 bytes | 20 bytes minimum |
| **Uses** | Suited for applications where speed and latency is more critical than reliability, such as streaming media (video, audio), online gaming, and DNS queries. | Used for applications where reliability and order are critical, such as web browsing (HTTP/HTTPS), email (SMTP, POP3, IMAP), and file transfers (FTP). |

