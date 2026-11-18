# Branch Office Network Topology (Cisco Packet Tracer)

##  Project Overview
This project contains a Cisco Packet Tracer (`.pkt`) file demonstrating a basic branch office network topology. It features inter-VLAN routing (Router-on-a-Stick), centralized DHCP, and separate VLANs for different departments.

##  File Included
* `Branch office.pkt` - The main Packet Tracer simulation file. *(Requires Cisco Packet Tracer 8.x or newer)*

##  Network Design & Topology
The network is segmented into four VLANs, using a single router to handle routing between them (Router-on-a-Stick).

### VLANs
| VLAN ID | Name | Purpose | Subnet |
|---------|------|---------|--------|
| **10** | SALES | Sales Department | `192.168.10.0/24` |
| **20** | HR | Human Resources | `192.168.20.0/24` |
| **30** | IT | IT Department | `192.168.30.0/24` |
| **99** | MGMT | Management | `192.168.99.0/24` |

## Configuration Details

### Router (R1)
**Interfaces:**
* `GigabitEthernet0/0/0`: `10.0.0.1` (Uplink/WAN)
* `GigabitEthernet0/0/1.10`: `192.168.10.1` (VLAN 10 Gateway)
* `GigabitEthernet0/0/1.20`: `192.168.20.1` (VLAN 20 Gateway)
* `GigabitEthernet0/0/1.30`: `192.168.30.1` (VLAN 30 Gateway)
* `GigabitEthernet0/0/1.99`: `192.168.99.2` (VLAN 99 Gateway)

**DHCP Pools:**
The router is configured as a DHCP server for all active VLANs. Current status shows 0 leased addresses, with 5 addresses excluded per pool (likely reserved for static IPs like servers or printers).
* **SALES_POOL**: `192.168.10.1 - 192.168.10.254`
* **HR_POOL**: `192.168.20.1 - 192.168.20.254`
* **IT_POOL**: `192.168.30.1 - 192.168.30.254`
* **MGMT_POOL**: `192.168.99.1 - 192.168.99.254`

### Switch
* **VLAN 1 (Default):** Ports `Gig1/0/6` through `Gig1/1/4`
* **VLAN 30 (IT):** Port `Gig1/0/5` (Connects to the IT network block)
* *Note: The `show vlan brief` output shows SALES and HR VLANs as active, but currently no specific access ports are assigned to them in the output provided.*

##  How to Use
1. Install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer).
2. Clone this repository or download the `.pkt` file.
3. Open the file in Packet Tracer.
4. Use the **Realtime** tab to watch DHCP assignments, or use the **Simulation** tab to trace packets.
