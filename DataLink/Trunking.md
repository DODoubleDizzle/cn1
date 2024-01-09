Trunking
1. **Definition**: VLAN trunking is a method used to transport multiple VLANs over a single network link. Trunking is typically used between switches, and between switches and routers or other network devices that support VLANs.
2. **Operation**:
    - **Trunk Ports**: On a switch, ports configured for trunking can carry traffic for multiple VLANs. These ports are typically connected to other switches or to routers.
    - **Tagging**: VLAN trunking often uses a tagging protocol like IEEE 802.1Q to identify the VLANs on the trunk link. Each frame on the trunk link is tagged with a VLAN identifier (ID) to indicate the VLAN to which it belongs.
    - **Handling Traffic**: When a trunk port receives traffic, it determines the VLAN based on the tag and forwards the traffic only to ports within that VLAN. If a frame is untagged, it is assigned to a default VLAN, typically VLAN 1.

- **Tagged vs. Untagged Ports**: In the context of VLAN trunking, ports on a switch can be either tagged or untagged. Tagged ports understand and use VLAN tags, while untagged ports belong to a single VLAN and do not use VLAN tags.
- **Native VLAN**: The native VLAN is a special VLAN on a trunk port that carries untagged traffic (VLAN ID =0). It's essential for backward compatibility with older devices that don't understand VLAN tags.
