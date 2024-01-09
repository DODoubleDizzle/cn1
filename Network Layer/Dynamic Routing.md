# Dynamic Routing
## How it works:
**Routing Protocols**: Routers use dynamic routing protocols like [[#Dijkstra]], RIP (Routing Information Protocol), OSPF (Open Shortest Path First), EIGRP (Enhanced Interior Gateway Routing Protocol), or BGP (Border Gateway Protocol) to exchange routing information.
**Routing Information Exchange**: Routers send out messages to neighbouring routers, informing them of their routing tables or changes in the network topology.
**Routing Table Updates**: Each router uses this information to update its routing table, choosing the best paths based on the protocol's algorithm (e.g., shortest path, least cost, fastest speed).
**Adaptation to Changes**: If there's a change in the network, such as a link failure, routers automatically recalculate routes and update their tables accordingly.
## Advantages of Dynamic Routing:
**Flexibility**: Automatically adapts to network changes, reducing the need for manual reconfiguration.
**Fault Tolerance**: Can quickly converge to a new path if a link or router fails.
**Load Balancing**: Some routing protocols can balance traffic load across multiple links to optimize network performance.
## Disadvantages of Dynamic Routing:
**Complexity**: Configuration and management can be more complex compared to static routing.**Resource Usage**: Consumes more CPU, memory, and network bandwidth due to constant exchange of routing information.
**Convergence Time**: In some cases, particularly with larger networks or less sophisticated protocols, it can take time for the network to converge (reach a stable state) after a change.