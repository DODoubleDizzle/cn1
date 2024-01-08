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
