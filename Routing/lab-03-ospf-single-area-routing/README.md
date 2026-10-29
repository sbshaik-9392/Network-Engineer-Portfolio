# Lab 03 - OSPF Single-Area Routing Between Three Routers

## Overview

This lab demonstrates the configuration and verification of Open Shortest Path First (OSPF) dynamic routing between three Cisco IOS routers in a single OSPF Area 0.

The topology contains three routers, each connected to a local LAN with a VPCS endpoint. Router02 uses an NM-1FE-TX network module to provide an additional Ethernet interface.

## Objectives

- Configure OSPF process 1 on three Cisco routers.
- Assign unique OSPF router IDs.
- Advertise LAN and inter-router networks in Area 0.
- Verify OSPF neighbor relationships.
- Examine routing tables and OSPF-learned routes.
- Verify end-to-end connectivity between VPCS endpoints.
- Document troubleshooting methods and key learning points.

## Topology

![OSPF Single-Area Routing Topology](topology.png)

**Topology:** VPCS01 — Router01 — Router02 — Router03 — VPCS03, with VPCS02 connected to Router02.

## IP Addressing Table

| Device | Interface | IP Address | Purpose |
|---|---|---|---|
| Router01 | FastEthernet0/0 | 192.168.1.1/24 | LAN 1 |
| Router01 | FastEthernet0/1 | 10.0.12.1/30 | Router01–Router02 link |
| Router02 | FastEthernet0/0 | 192.168.2.1/24 | LAN 2 |
| Router02 | FastEthernet0/1 | 10.0.12.2/30 | Router01–Router02 link |
| Router02 | FastEthernet1/0 | 10.0.23.1/30 | Router02–Router03 link |
| Router03 | FastEthernet0/0 | 192.168.3.1/24 | LAN 3 |
| Router03 | FastEthernet0/1 | 10.0.23.2/30 | Router02–Router03 link |
| VPCS01 | NIC | 192.168.1.10/24 | Default gateway: 192.168.1.1 |
| VPCS02 | NIC | 192.168.2.10/24 | Default gateway: 192.168.2.1 |
| VPCS03 | NIC | 192.168.3.10/24 | Default gateway: 192.168.3.1 |

## OSPF Configuration Summary

| Parameter | Value |
|---|---|
| Routing protocol | OSPF |
| OSPF process ID | 1 |
| OSPF area | Area 0 |
| Router01 Router ID | 1.1.1.1 |
| Router02 Router ID | 2.2.2.2 |
| Router03 Router ID | 3.3.3.3 |

The detailed router configurations will be provided in the `configs/` directory.

## Verification

The following evidence will document the lab's actual verification results:

- OSPF neighbor adjacency.
- OSPF interface participation.
- Routing tables and OSPF-learned routes.
- End-to-end ICMP ping tests between VPCS endpoints.

See the `verification/` directory for command outputs and test results.

## Troubleshooting

Troubleshooting notes, observed issues, root causes, and resolutions will be documented in `troubleshooting/README.md`.

## Key Learning Points

- OSPF dynamic routing fundamentals.
- Router IDs and OSPF neighbor relationships.
- OSPF Area 0 and wildcard masks.
- OSPF-learned routes in the routing table.
- End-to-end connectivity verification.
- Structured routing troubleshooting.

## Lab Status

The lab configuration and verification evidence will be documented using actual outputs from the EVE-NG environment.
