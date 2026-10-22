# Lab 02: Static Routing Configuration Between Two Routers

## Overview

This lab demonstrates IPv4 static routing between two Cisco routers to enable end-to-end connectivity between two separate LAN networks.

The topology consists of two Cisco routers (Router01 and Router02) and two VPCS nodes (Node3 and Node4), built and tested in EVE-NG.

## Objectives

- Configure IPv4 addressing on router interfaces and end devices.
- Understand directly connected routes and static routes.
- Configure static routing using next-hop addresses.
- Analyze routing tables and route selection.
- Verify end-to-end connectivity using ICMP ping.
- Understand TTL behavior during packet forwarding.
- Troubleshoot routing and connectivity issues.

## Topology

**Devices:** 2 Cisco routers and 2 VPCS nodes.

Topology screenshot: `topology.png` (to be uploaded in this directory).

## IP Addressing

| Device | Interface | IP Address | Purpose |
|---|---|---|---|
| Router01 | FastEthernet0/0 | 192.168.1.1/24 | LAN 1 gateway |
| Router01 | FastEthernet0/1 | 10.0.0.1/30 | Inter-router link |
| Router02 | FastEthernet0/1 | 10.0.0.2/30 | Inter-router link |
| Router02 | FastEthernet0/0 | 192.168.2.1/24 | LAN 2 gateway |
| Node3 | Ethernet | 192.168.1.10/24 | LAN 1 host |
| Node4 | Ethernet | 192.168.2.10/24 | LAN 2 host |

### Default Gateways

- Node3: `192.168.1.1`
- Node4: `192.168.2.1`

## Technologies and Concepts

- IPv4 addressing and subnetting
- Directly connected routes
- Static routing and next-hop selection
- Routing table analysis
- ICMP ping verification
- TTL analysis
- End-to-end packet flow

## Packet Flow

For communication from Node3 to Node4:

1. Node3 identifies that `192.168.2.10` is outside its local subnet and sends the packet to its default gateway, `192.168.1.1`.
2. Router01 checks its routing table and forwards the packet toward Router02 using the configured static route.
3. Router02 receives the packet over the inter-router link and forwards it to its directly connected LAN `192.168.2.0/24`.
4. Node4 receives the packet and returns the ICMP reply through its default gateway.
5. The return packet follows the route configured on Router02 toward Router01 and then reaches Node3.

## Configuration Files

- [Router01 Configuration](configs/router01-config.txt)
- [Router02 Configuration](configs/router02-config.txt)

## Verification Evidence

- [Routing and Connectivity Verification](verification/README.md)
- [Router01 Routing Table](verification/router01-routing-table.txt)
- [Router02 Routing Table](verification/router02-routing-table.txt)

## Troubleshooting

- [Static Routing Troubleshooting Guide](troubleshooting/README.md)

## Lab Outcome

Successfully configured static routes between two routers and verified the reported end-to-end connectivity between the two LANs using ICMP ping tests.
