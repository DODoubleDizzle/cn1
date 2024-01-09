
# Network management
## FACPS
### Fault Management
This involves the detection, isolation, and correction of network problems. It includes identifying issues, localizing their source, isolating them for detailed analysis, and then resolving these faults. The goal is to increase network reliability and reduce the mean time to repair (MTTR).

### Configuration Management
This entails managing the network's configuration settings, including the documentation, versioning, and tracking of changes to the network's configuration. Configuration management tools often include IP address management (IPAM), configuration management databases (CMDBs), and operational support systems (OSS).

### Accounting (or Administration) Management
This aspect of network management focuses on measuring network usage, generating statistics, tracking services, and billing. This can be based on usage or service types and may involve managing groups or individual user accounts.

### Performance Management
Performance management ensures that the network performs optimally. This includes monitoring throughput, response time, jitter, utilization, packet loss rates, and other performance metrics. It also encompasses capacity planning, generating reports, and maintaining historical records.

### Security Management
Involves collecting, analysing, and managing security-related information. This can include access logs, event analysis, and security audits to protect the network against unauthorized access and other security threats.

## Old school protocols
### SNMP
SNMP operates primarily over UDP ports 161 and 162 (for SNMP traps, which are alerts when specific events or errors occur on the network devices). SNMP uses a Management Information Base (MIB), which is a hierarchically organized collection of Object Identifiers (OIDs). These OIDs can be scalar or tabular in type.
SNMP allows network administrators to monitor the health and performance of network devices like routers, switches, servers, and other network appliances. 
It gathers data about bandwidth usage, system performance, and network traffic patterns from SNMP-enabled devices.
Administrators can use SNMP to configure network devices remotely. This includes tasks like changing settings or updating firmware.

### Syslog
Syslog is a protocol developed in the 1980s (RFC 3164 in 2001) for sending logging messages or events from devices to a server. It is primarily used for network and system logging. The protocol operates over UDP port 514. Syslog messages are categorized into different severity levels, ranging from 0 (Emergency) to 7 (Debugging), allowing for efficient categorization and filtering of log data based on its importance or urgency.

The severity levels are

| 0 | Emergency | System is unusable |
| ---- | ---- | ---- |
| 1 | Alert | Immediate action is needed |
| 2 | Critical | Software / hardware failure |
| 3 | Error | general error |
| 4 | Warning | not an error but still problem |
| 5 | Notification |  |
| 6 | Information | Routine information |
| 7 | Debugging | Debug stuff |

The format of a Syslog message typically includes:

- **PRI (Priority)**: A code that combines the facility code and the severity level, ranging from 3 to 5 characters.
- **Header**: This part contains the timestamp and the hostname or IP address of the device sending the message.
- **MSG**: The actual message content, which provides detailed information about the event or issue reported.

### NetFlow
NetFlow is a network protocol used for collecting and monitoring IP network traffic as it enters or exits an interface. Here are the key components of a NetFlow record:

1. **Source IP Address**: The IP address of the device that originated the traffic.
2. **Destination IP Address**: The IP address of the device that is the intended recipient of the traffic.
3. **Source Port Number**: The port number on the source device.
4. **Destination Port Number**: The port number on the destination device.
5. **Layer 3 Protocol Type**: The type of Internet layer protocol used (e.g., TCP, UDP).
6. **Type of Service (ToS)**: A field that specifies the priority and handling of the traffic.
7. **Input Logical Interface**: The interface through which the traffic entered the network device.