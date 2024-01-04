# Table of contents
- [[Copper Cables]]
	- [[Copper Cables#Twisted Pair Cables|Twisted Pair Cables]]
	- [[Copper Cables#Coaxial Cables|Coaxial Cables]]
- [[Fiber Optic|Fiber Optic Cables]]
	- [[Fiber Optic#Single-Mode Fiber (SMF)|Single-Mode Fiber (SMF)]]
	- [[#Fiber Optic#Multi-Mode Fiber (MMF)|Multi-Mode Fiber (MMF)]]
	- [[#Fiber Optic#Key Differences Between SMF and MMF|Key Differences Between SMF and MMF]]
	- [[Fiber Optic#Eye Diagram|Eye Diagram]]
	- [[Fiber Optic#Attenuation|Attenuation]]
	- [[Fiber Optic#Dispersion|Dispersion]]
	- [[Fiber Optic#The 3R's|The 3R's]]
- [[Wireless]]
	- [[Wireless#Signal-to-Noise Ratio (SNR)|Signal-to-Noise Ratio (SNR)]]
	- [[Wireless#Power Management|Power Management]]
	- [[Wireless#Standards|Standards]]
- [[Encoding]]
	- [[Encoding#Clocking|Clocking]]
	- [[Encoding#Self-Clocking Signals|Self-Clocking Signals]]
	- [[Encoding#Non-Self-Clocking Signals|Non-Self-Clocking Signals]]
	- [[Encoding#Manchester Encoding|Manchester Encoding]]
	- [[Encoding#NRZ (Non-Return to Zero)|NRZ (Non-Return to Zero)]]
	- [[Encoding#RZ (Return to Zero)|RZ (Return to Zero)]]
	- [[Encoding#8B/10B Encoding|8B/10B Encoding]]
	- [[Encoding#LLC (Logical Link Control)|LLC (Logical Link Control)]]
	- [[Encoding#MAC (Medium Access Control)|MAC (Medium Access Control)]]


# Copper Cables
Copper cables are widely used for networking and telecommunications due to their cost-effectiveness and reliability. The two main types are twisted pair and coaxial cables.

#### Twisted Pair Cables
![[Pasted image 20240103094907.png]]
- **Structure**: Consists of pairs of insulated copper wires twisted together.
- **Types**:
    - **Unshielded Twisted Pair (UTP)**: No additional shielding, more susceptible to electromagnetic interference (EMI). Common in Ethernet networks (CAT5, CAT6).
    - **Shielded Twisted Pair (STP)**: Includes a foil shield to reduce EMI. Used in environments with high interference.
- **Categories**: Vary based on data transmission speed and bandwidth. For example, CAT5e supports up to 1 Gbps, while CAT6 supports up to 10 Gbps over short distances.
- **Applications**: Common in local area networks (LANs), telephone systems.

#### Coaxial Cables
![[Pasted image 20240103080934.png]]
- **Structure**: A single copper conductor at the center, surrounded by a plastic layer for insulation, a metallic foil or braided shield, and an outer plastic covering.
- **Types**:
    - **RG-6**: Used for cable television, internet, and other data transmissions.
    - **RG-59**: Commonly used for closed-circuit television (CCTV) applications.
- **Benefits**: Better shielding compared to twisted pair cables, making them less susceptible to EMI and suitable for longer distances.
- **Applications**: Broadband internet, cable television, Ethernet backbones.
    
# Fiber Optic Cables
Fiber optic cables use light to transmit data at 2/3 the light speed over long distances, offering significally higher bandwidth than copper cables.
#### Single-Mode Fiber (SMF)
- **Structure**: Has a small core (about 9 micrometers in diameter) that allows only one mode (path) of light to propagate.
- **Light Propagation**: The small core limits light reflection, allowing the light to travel directly down the fiber.
- **Benefits**: Lower attenuation (signal loss), higher bandwidth, capable of transmitting over longer distances (tens to hundreds of kilometers).
- **Applications**: Long-haul telecommunication networks, high-speed data connections.
#### Multi-Mode Fiber (MMF)
- **Structure**: Larger core size (typically 50 or 62.5 micrometers) than SMF, allowing multiple modes of light to propagate.
- **Light Propagation**: The larger core size causes more light reflection and dispersion, limiting the transmission distance.
- **Benefits**: Easier to work with (light sources and connectors are less expensive and more tolerant to alignment errors) but with limited distance and bandwidth compared to SMF.
- **Applications**: Short-range communication applications like within buildings or campuses, data center connections. Maximum 500m.

#### Key Differences Between SMF and MMF
- **Core Size**: SMF has a much smaller core allowing only one light mode, while MMF has a larger core allowing multiple light modes.
- **Transmission Distance**: SMF is suitable for long-distance transmission, whereas MMF is used for shorter distances.
- **Bandwidth and Data Rate**: SMF offers higher bandwidth and data rates.
- **Cost**: SMF tends to be more expensive in terms of the fiber itself and the technology required to use it (e.g., light sources, connectors).

### Eye Diagram
An eye diagram is a tool used for analyzing the quality and performance of a digital signal. It's created by layering successive segments of a signal to form a composite image.
- The clarity of the eye opening in the diagram indicates the quality of the signal. A well-defined and wide open eye suggests minimal signal distortion and thus a good transmission system.
- Used for analyzing signal integrity, timing errors, and potential data corruption.
- Horizontal shift is called jitter, which can be caused by imprecise clocks

![[Pasted image 20240103081502.png]]


### Attenuation
Attenuation refers to the reduction in signal strength as it travels through a medium.
![[Pasted image 20240103093806.png]]
- **Copper cables** it's often due to resistance
- Absorption
	- **Energy Conversion**: As light passes through the fiber, some of its energy is absorbed by the material and converted into heat.
	- **Wavelength Dependence**: The extent of material absorption can vary with the wavelength of the light. For instance, certain wavelengths in the infrared region are more strongly absorbed by silica. 
	- **Water Peak** / Experimental:
	    - There is a region known as the "water peak" / "Experimental" where residual water in the fiber core can cause increased absorption. This peak is particularly noticeable around **1240 nm to 1380 nm and 950nm to 1.1nm**
	- **Ultraviolet (UV) Absorption**:
	    - Below **400 nm**: Silica fibers exhibit strong absorption in the UV range. This is due to electronic transitions in the silicon dioxide molecules.
	    - This range is outside the standard operating wavelengths for most fiber optic systems.
	- **Infrared Absorption**:
	    - Above **1600 nm**: As the wavelength enters the infrared region, absorption increases due to the fundamental vibrational modes of the silica molecules themselves.
	    - This increase in absorption limits the use of wavelengths beyond 1600 nm for long-distance communication in standard silica fibers.
	
- **Rayleigh scattering** refers to the scattering of light by particles in its path
- Bending
	- Microbends (small distortions in manufacturing)
	- Macrobends (wrapping fiber around a corner)
- Back reflections
- Fiber splices
- Mechanical connections
Greater distances and higher frequencies typically lead to more significant attenuation.

### Dispersion
Dispersion in fiber optics is the spreading of light pulses over time, which can lead to signal degradation.
- **Modal Dispersion**: Occurs in multi-mode fibers due to different light paths (modes) taking different times to traverse the fiber.
- **Chromatic Dispersion**: Arises from the different speeds of light wavelengths in single-mode fibers.
- **Polarization Mode Dispersion**: Occurs in single-mode fibers due to imperfections, causing different polarizations of light to travel at different speeds.

### The 3R's
**Re-amplifying**: Boosting the signal strength to overcome attenuation.
**Reshaping**: Correcting distortions in the signal waveform.
**Retiming**: 
- **Purpose**: To correct timing errors and jitter that have accumulated in the signal over the transmission path to ensure that the signal remains within its designated time slot.
- **Process**: The timing of the signal is realigned with the network's master clock.

# Wireless
### Signal-to-Noise Ratio (SNR)
SNR is a measure, representing the level of the desired signal relative to the background noise level. Higher SNR indicates a clearer signal. A low SNR might result in poor connection quality and slower speeds.

### Power Management
In wireless networking, managing the power consumption of devices is crucial, especially for mobile devices. Power management techniques include adjusting the transmission power, implementing sleep modes, and using power-efficient protocols. This ensures longer battery life while maintaining adequate network performance.

### Standards
**Wi-Fi (IEEE 802.11)**
- **Purpose**: Provides high-speed wireless Internet access over short distances.
- **Usage**: Common in homes, offices, and public hotspots.
**802.11a**:
- **Frequency**: Operates in the 5 GHz band. / **Speed**: Offers up to 54 Mbps.
- **Range**: Shorter range due to higher frequency.
- **Notable Features**: Less prone to interference from other household devices but has limited penetration through walls.
**802.11b**:
- **Frequency**: Operates in the 2.4 GHz band. / **Speed**: Offers up to 11 Mbps.
- **Range**: Better range than 802.11a.
- **Notable Features**: More susceptible to interference from other devices like microwaves and cordless phones.
**802.11g**:
- **Frequency**: Operates in the 2.4 GHz band. / **Speed**: Offers up to 54 Mbps.
- **Range**: Similar to 802.11b.
- **Notable Features**: Backward compatible with 802.11b, providing a balance of speed and range.
**802.11n (Wi-Fi 4)**:
- **Frequency**: Operates in both 2.4 GHz and 5 GHz bands.
- **Speed**: Offers up to 600 Mbps (using four spatial streams).
- **Range**: Improved range over previous standards.
- **Notable Features**: Introduced MIMO (Multiple Input Multiple Output) technology for improved data throughput and signal reliability.
**802.11ac (Wi-Fi 5)**:
- **Frequency**: Primarily in the 5 GHz band.
- **Speed**: Offers multi-station WLAN throughput of at least 1 Gbps and a single link throughput of at least 500 Mbps.
- **Range**: Similar to 802.11n, but faster speeds at shorter distances.
- **Notable Features**: Supports MU-MIMO (Multi-User MIMO), allowing more devices to operate simultaneously without sacrificing bandwidth.
**802.11ax (Wi-Fi 6)**:
- **Frequency**: Operates in both 2.4 GHz and 5 GHz bands.
- **Speed**: Offers increased speeds (potentially exceeding 10 Gbps), efficiency, and throughput.
- **Range**: Improved performance in environments with many connected devices.
- **Notable Features**: Introduces OFDMA (Orthogonal Frequency Division Multiple Access) for better channel utilization, target wake time (TWT) for improved power efficiency, and BSS (Basic Service Set) coloring for mitigating interference.
    
**LTE (Long Term Evolution) and 5G**:
- **Purpose**: High-speed mobile communication.
- **Usage**: Mobile phones, data terminals, and broadband wireless access.
- **Features**: LTE offers fast data rates and improved capacity. 5G further enhances speed, reduces latency, and supports massive IoT and critical communications.
    
**NFC (Near Field Communication)**:
- **Purpose**: Very short-range wireless communication.
- **Usage**: Contactless payment systems, electronic ticket smartcards, and simple data exchange between devices.
- **Features**: Extremely short range (a few centimeters), designed for secure transactions.
    
**RFID (Radio-Frequency Identification)**:
- **Purpose**: Wireless identification and tracking.
- **Usage**: Inventory management, asset tracking, and identification applications.
- **Features**: Passive tags don’t require a power source. Used for automated tracking of objects.
    
**LoRa (Long Range)**:
- **Purpose**: Long-range, low-power wireless platform.
- **Usage**: IoT, smart cities, and industrial applications.
- **Features**: Long range (5km - 15km), low power, ideal for sensors and low-bandwidth applications.
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