# Network Documentation

## Project Scope
A two-building enterprise network implemented in Cisco Packet Tracer.

## Design Goals
- Department and service segmentation.
- Dynamic routing between network segments.
- Gateway redundancy.
- Redundant Layer 2 connectivity.
- ACL-based traffic control.
- Firewall and simulated Internet edge integration.

## Core Redundancy
Each building uses two core switches. HSRP provides the virtual default gateway, while STP and EtherChannel manage redundant Layer 2 connectivity.

## EtherChannel
LACP Port-channel1 was implemented between the core switches in both buildings using bundled FastEthernet links.

## STP Design
STP root primary and secondary roles were assigned to provide deterministic forwarding behavior and a backup root bridge.

## Routing
OSPF process 1 was used for dynamic route exchange across the routed enterprise infrastructure. The ASA firewall was also configured with OSPF on its implemented transit networks.

## Security
Traffic controls are based on extended ACLs and network segmentation. The implemented ACL naming includes SERVER-ACL, PRINTER-ACL, CCTV-ACL, and SALES-ACL.

## Server Network
VLAN 60 is used for server services. A monitoring-server role is reserved in the design, but a full Zabbix/PRTG implementation was not performed inside Packet Tracer.

## Evidence
Operational validation should be stored in the `evidence/` directory as screenshots from the actual Packet Tracer environment.
