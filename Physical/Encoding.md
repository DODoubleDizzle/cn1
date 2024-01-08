# Encoding
### Clocking
Clocking refers to the synchronization mechanism that determines when data should be sent or received. It's essential because it helps the receiver know when to expect each bit of data.

### Self-Clocking Signals 
These are signals where timing information is present within the signal itself. In other words, the signal provides enough transitions (changes from high to low or low to high) for the receiver to maintain synchronization with the sender's clock.
- **Advantages**: The primary advantage of self-clocking signals is that they simplify the design of communication systems as they do not require a separate line for clock data.
- **Examples**: Manchester encoding, 8B/10B, RZ.

### Non-Self-Clocking Signals
In non-self-clocking signals, the timing information is not included in the signal. Instead, the sender and receiver must rely on an external clock source to stay in sync. This can be achieved through a separate clock line or by assuming that both sender and receiver are operating at exactly the same frequency (which can be risky in practice due to frequency drift).
- **Advantages**: Non-self-clocking signals can be more efficient in terms of bandwidth utilization. Since they don't require extra transitions for clocking, they can pack data more densely compared to self-clocking signals.
- **Examples**: NRZ (Non-Return to Zero) is a common non-self-clocking scheme. In NRZ, the signal stays at a high or low level during the entire bit period without any additional transitions to indicate the clock.

### Manchester Encoding 
![[Pasted image 20240103092240.png]]
This is a method of encoding where each bit of data is represented by two level transitions. A logical '0' might be represented by a transition from high to low, and a logical '1' by low to high, or vice versa, depending on the convention used. Manchester encoding ensures that there's a transition in the middle of each bit, aiding in clock synchronization between the sender and receiver.

### RZ (Return to Zero)
![[Pasted image 20240103092402.png]]
RZ encoding is similar to NRZ but with a key difference: the signal returns to zero (baseline voltage) midway through each bit period. This makes it easier to synchronize the clock but doubles the bandwidth required compared to NRZ.

### NRZ (Non-Return to Zero)
![[Pasted image 20240103092419.png]]
NRZ encoding is a way of representing data where the signal level (high or low) directly represents the bit value (1 or 0). In NRZ, the signal doesn't return to zero (the baseline voltage) between bits. There are two main types: NRZ-L (Level) where the signal level is constant during the bit interval, and NRZ-I (Inverted) where a transition occurs if the next bit is different.

### 8B/10B Encoding
This encoding method converts 8-bit data into 10-bit symbols. The primary purpose of 8B/10B encoding is to balance the number of 1s and 0s in the data stream, thereby reducing the DC bias (accumulation of voltage in one direction) and providing enough transitions to maintain clock synchronization. It's commonly used in high-speed data transmission standards like Gigabit Ethernet and Fibre Channel.

### LLC (Logical Link Control) 
In the IEEE 802 networking framework, the LLC sublayer is part of the data link layer. It provides multiplexing mechanisms that allow multiple network protocols to coexist within a multi-access network and can offer flow and error control.

### MAC (Medium Access Control)
The MAC sublayer is also part of the data link layer and is responsible for controlling how devices in a network gain access to the medium and permission to transmit data. It addresses and channels data, and it handles collision detection and retransmission in Ethernet networks.