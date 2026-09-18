# Enterprise Multi-Building Network Infrastructure

A hands-on Cisco Packet Tracer project demonstrating enterprise network design, Layer 2/Layer 3 connectivity, segmentation, routing, redundancy, security controls, and systematic troubleshooting.

## Project Overview

This project models a two-building enterprise network with redundant core switching, routed connectivity, gateway redundancy, an edge router, Cisco ASA firewall integration, and a simulated ISP/Internet segment.

The repository is intended as technical portfolio evidence for Junior Network Engineer, Network Support Engineer, NOC, and Network Administrator roles.

## Objectives

- Design a scalable multi-building enterprise topology.
- Segment departments and services with VLANs.
- Provide inter-VLAN connectivity.
- Provide centralized DHCP services.
- Implement OSPF dynamic routing.
- Provide gateway redundancy with HSRP.
- Build resilient Layer 2 paths with STP and LACP EtherChannel.
- Apply ACL-based traffic controls.
- Integrate a Cisco ASA firewall and simulated Internet edge.
- Validate connectivity and troubleshoot failures using Cisco IOS/ASA commands.

## VLAN & IP Addressing

| VLAN | Department / Service | Network |
|---:|---|---|
| 10 | Reception | 192.168.10.0/27 |
| 20 | Sales | 192.168.20.0/27 |
| 30 | Finance | 192.168.30.0/27 |
| 40 | HR | 192.168.40.0/27 |
| 50 | Management | 192.168.50.0/27 |
| 60 | Servers | 192.168.60.0/27 |
| 70 | Wireless | 192.168.70.0/27 |
| 80 | Printer | 192.168.80.0/27 |
| 90 | CCTV | 192.168.90.0/27 |

### VTP Domains

- Building 1: BOLDING1
- Building 2: BOLDING2

The two buildings are maintained as separate VTP domains.

## Architecture

Each building uses two core switches. The core layer provides Layer 3 connectivity and HSRP gateway redundancy. Redundant Layer 2 links are bundled with LACP EtherChannel, while STP controls loop prevention and forwarding roles.

The enterprise edge connects the internal network to a Cisco ASA firewall and a simulated ISP/Internet segment.

## Technologies

### Switching & Segmentation
- VLANs
- 802.1Q trunking
- Network segmentation
- STP Root Primary / Secondary
- PortFast
- BPDU Guard
- LACP EtherChannel

### Routing & Services
- Inter-VLAN routing
- Static routing
- OSPF
- DHCP
- HSRP

### Security & Edge
- Extended ACLs
- SERVER-ACL
- PRINTER-ACL
- CCTV-ACL
- SALES-ACL
- Cisco ASA
- NAT/PAT
- Simulated ISP/Internet edge

### Wireless & Servers
- Dedicated Server VLAN
- Dedicated Wireless VLAN design
- Monitoring-server concept

## High Availability

- HSRP provides a virtual default gateway and gateway failover.
- LACP EtherChannel combines physical links into logical Port-Channels and provides link resilience.
- STP prevents Layer 2 loops and provides controlled failover across redundant paths.

## Validation

The implementation was validated using operational checks including show ip route, show standby brief, show etherchannel summary, show spanning-tree vlan 10, show ip ospf neighbor, show route, show interface ip brief, ping, and traceroute.

Validation focused on HSRP roles, EtherChannel status, STP root and forwarding roles, OSPF neighbor adjacency and route exchange, interface and VLAN status, end-to-end connectivity, ACLs, and ASA behavior.

## Troubleshooting Method

1. Check physical and interface status.
2. Verify VLAN membership and trunking.
3. Check STP state.
4. Verify HSRP roles.
5. Verify EtherChannel bundling.
6. Check OSPF neighbors and routing tables.
7. Verify ASA interfaces and routes.
8. Test end-to-end connectivity.
9. Apply one change at a time and re-validate.

## Monitoring

A monitoring-server concept is reserved in the Server VLAN. A full Zabbix/PRTG deployment was not implemented inside Packet Tracer and is therefore treated as a real-lab extension rather than completed functionality.

## Repository Structure

- README.md
- FINAL.png
- the final project bkt1.pkt
- docs/network-documentation.md
- evidence/README.md

## Evidence

See docs/network-documentation.md for the design documentation and evidence/README.md for the recommended validation screenshots. Only evidence produced from the actual final Packet Tracer configuration should be added.

## Future Improvements

- Add final validation screenshots.
- Implement Zabbix or PRTG in a real lab environment.
- Add SNMP-based monitoring and alerting.
- Add automated configuration backup.
- Continue documenting Internet-edge behavior and security validation.

---

Portfolio focus: Enterprise Networking • Cisco IOS • Routing & Switching • Network Security • Troubleshooting
