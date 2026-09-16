# Enterprise Multi-Building Network Infrastructure

> Hands-on Cisco Packet Tracer project focused on enterprise network engineering, switching, routing, segmentation, troubleshooting, redundancy, and validation.

## Overview
This project demonstrates the design and implementation of a multi-building enterprise network. The primary focus is network engineering: Layer 2/Layer 3 connectivity, VLAN segmentation, dynamic routing, gateway redundancy, link resilience, access control, and systematic troubleshooting.

The topology connects two buildings through a routed infrastructure and includes redundant core switching, an edge router, a Cisco ASA firewall, and a simulated ISP/Internet segment.

## Network Engineering Objectives
- Segment departments and services using VLANs.
- Provide inter-VLAN communication and automatic addressing with DHCP.
- Implement dynamic routing with OSPF.
- Provide default-gateway redundancy using HSRP.
- Increase link resilience with LACP EtherChannel.
- Control redundant Layer 2 paths using STP root primary/secondary roles.
- Apply ACL-based traffic controls and network segmentation.
- Integrate a Cisco ASA firewall and simulated Internet edge.
- Provide dedicated Server and Wireless VLANs.

## VLAN and IP Addressing
| VLAN | Department / Service | Network |
|---|---|---|
| 10 | Reception | 192.168.10.0/27 |
| 20 | Sales | 192.168.20.0/27 |
| 30 | Finance | 192.168.30.0/27 |
| 40 | HR | 192.168.40.0/27 |
| 50 | Management | 192.168.50.0/27 |
| 60 | Servers | 192.168.60.0/27 |
| 70 | Wireless | 192.168.70.0/27 |
| 80 | Additional segmented network | 192.168.80.0/27 |
| 90 | Additional segmented network | 192.168.90.0/27 |

## Architecture
The design uses two redundant core switches in each building. Core switches provide Layer 3 connectivity and HSRP-based gateway redundancy. Redundant links between core devices are bundled using LACP EtherChannel, while STP controls Layer 2 forwarding and failover paths.

The routed edge connects the internal enterprise infrastructure to a Cisco ASA firewall and a simulated ISP/Internet segment.

## Technologies Implemented

### Switching and Segmentation
- VLANs
- 802.1Q trunking
- Network segmentation
- Spanning Tree Protocol
- STP Root Primary / Secondary
- LACP EtherChannel
- PortFast and BPDU Guard

### Routing and Network Services
- Inter-VLAN routing
- Static routing
- OSPF
- DHCP
- HSRP

### Network Security and Edge
- Extended ACLs
- SERVER-ACL
- PRINTER-ACL
- CCTV-ACL
- SALES-ACL
- Cisco ASA Firewall
- NAT/PAT
- Simulated ISP/Internet edge

### Wireless and Servers
- Dedicated Server VLAN
- Dedicated Wireless VLAN design for each building

## High Availability
**HSRP** provides virtual default-gateway redundancy for VLAN clients.

**LACP EtherChannel** combines physical links into logical Port-Channels so connectivity can continue through remaining member links when an individual member fails.

**STP** prevents Layer 2 loops and controls redundant forwarding paths through root primary and secondary roles.

## Validation
Operational commands used to validate the implementation include:

```text
show ip route
show standby brief
show etherchannel summary
show spanning-tree vlan 10
show ip ospf neighbor
show route
show interface ip brief
ping
traceroute
```

Validation covered HSRP roles, LACP EtherChannel status, STP root/forwarding roles, OSPF neighbor adjacency and route exchange, VLAN/interface status, and end-to-end connectivity checks.

## Troubleshooting Approach
Issues were diagnosed before configuration changes by checking:

1. Physical and interface status.
2. VLAN and trunk connectivity.
3. STP forwarding state.
4. HSRP Active/Standby state.
5. EtherChannel bundle status.
6. OSPF neighbors and routing tables.
7. ASA routing and interface reachability.

Changes were made incrementally and verified with Cisco IOS/ASA operational output.

## Monitoring
A monitoring-server concept was included in the Server VLAN. Full Zabbix or PRTG deployment is listed as a future real-lab improvement because Packet Tracer does not provide a full implementation environment for those platforms.

## Tools
- Cisco Packet Tracer
- Cisco IOS / CLI
- Cisco ASA

## Skills Demonstrated
VLANs, trunking, inter-VLAN routing, static routing, DHCP, ACLs, OSPF, HSRP, STP, LACP EtherChannel, Cisco ASA, NAT/PAT, network segmentation, wireless network design, redundancy, troubleshooting, and network validation.

## Repository Structure
```text
enterprise-multi-building-network/
├── README.md
├── docs/
│   └── network-documentation.md
└── evidence/
    └── README.md
```

## Future Improvements
- Implement real monitoring using Zabbix or PRTG outside Packet Tracer.
- Add centralized monitoring and alerting using SNMP in a real lab.
- Add automated configuration backup procedures.
- Continue investigating simulated Internet-edge behavior in Packet Tracer.

---
Built as hands-on technical evidence for entry-level Network Engineering, Network Support, and Network Administration roles.
