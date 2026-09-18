# Enterprise Network Documentation

## 1. Scope

A two-building enterprise network implemented in Cisco Packet Tracer.

The design focuses on segmentation, resilient switching, dynamic routing, gateway redundancy, traffic control, firewall integration, and operational validation.

## 2. Design Goals

- Department and service segmentation.
- Inter-VLAN connectivity.
- Dynamic routing between routed network segments.
- Default-gateway redundancy.
- Redundant Layer 2 connectivity.
- ACL-based traffic control.
- Cisco ASA and simulated Internet-edge integration.
- Repeatable troubleshooting and validation.

## 3. VLAN Plan

| VLAN | Function | Network |
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

The two buildings are treated as separate VTP domains.

## 4. Switching Design

Each building uses two core switches.

### EtherChannel

LACP EtherChannel is used between core switches to combine physical links into logical Port-Channels and improve link resilience.

### STP

STP is used to prevent Layer 2 loops and provide deterministic forwarding behavior. Root primary and secondary roles are used to control the preferred and backup spanning-tree roots.

PortFast and BPDU Guard are applied where appropriate for edge/access ports.

## 5. Routing & Gateway Redundancy

### Inter-VLAN Routing

Layer 3 core devices provide connectivity between VLANs.

### OSPF

OSPF process 1 is used for dynamic route exchange across the routed enterprise infrastructure.

### HSRP

HSRP provides a virtual default gateway for client VLANs and supports Active/Standby gateway redundancy.

## 6. DHCP

DHCP provides automatic addressing for client networks. Where the DHCP server is located on a different subnet, DHCP relay/IP helper functionality is used to forward client DHCP requests toward the server.

## 7. Security

Traffic controls are implemented using extended ACLs and network segmentation.

Implemented ACL naming includes:

- SERVER-ACL
- PRINTER-ACL
- CCTV-ACL
- SALES-ACL

The edge also includes Cisco ASA firewall integration and NAT/PAT for the simulated Internet environment.

## 8. Server & Monitoring Network

VLAN 60 is reserved for server services.

A monitoring-server role is included in the design. Full Zabbix/PRTG deployment is intentionally not claimed as completed because Packet Tracer does not provide the same monitoring environment as a real network lab.

## 9. Validation Commands

Useful operational checks include:

- show vlan brief
- show interfaces trunk
- show spanning-tree
- show etherchannel summary
- show standby brief
- show ip interface brief
- show ip route
- show ip ospf neighbor
- show access-lists
- show route
- ping
- traceroute

## 10. Troubleshooting Workflow

1. Check interface status.
2. Verify VLAN membership.
3. Verify trunk configuration.
4. Check STP forwarding state.
5. Check EtherChannel membership.
6. Verify HSRP state.
7. Verify OSPF adjacency.
8. Check routing tables.
9. Verify ACL and ASA behavior.
10. Test end-to-end connectivity.

Changes should be made incrementally and verified after each major configuration change.

## 11. Evidence

Store screenshots from the actual final Packet Tracer environment under evidence/. The evidence checklist is maintained in evidence/README.md.

## 12. Known Scope Limitations

- Packet Tracer is a simulation environment.
- Zabbix/PRTG is not presented as implemented functionality in this repository.
- Internet-edge behavior should be validated against the actual Packet Tracer topology rather than assumed from the documentation.
