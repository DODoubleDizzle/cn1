# Static Routing
## How it Works:
Static routing has two key components:
**Routing Table**: The network administrator manually enters routes into the routing table. Each route typically includes the destination network, the subnet mask, and the next-hop address or exit interface.
**Data Forwarding**: When a router receives a packet, it checks its routing table to determine where to forward the packet. The router looks for a network address in the routing table that matches the destination address of the packet and forwards the packet accordingly. If there is no default gateway the packet is dropped and an error is returned.

## Use Cases:
**Small Networks**: Ideal for small networks where the network topology is simple and does not change frequently.
**Single Path**: When there is only one path to a destination, static routing can be an efficient choice.
**Controlled Environments**: In environments where network security and the predictability of the routing path are crucial, static routing offers a controlled way to manage traffic.

## Advantages of Static Routing:
- **Simplicity**: Easier to understand and manage in smaller networks.
- **No fluctuating routes**
- **Security**: Since routes are not advertised, it offers a degree of security.
- **Resource Efficiency**: Less CPU and bandwidth usage.

## Disadvantages of Static Routing:
- **Scalability Issues**: Not suitable for large or rapidly changing networks due to the administrative overhead of manual configuration.
- **Lack of Fault Tolerance**: Static routes do not automatically adjust to network changes or failures.
- **Administrative Overhead**: Requires manual intervention to update routes when network changes occur.
