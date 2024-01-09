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
