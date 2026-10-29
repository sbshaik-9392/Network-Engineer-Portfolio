# Lab 04: OSPF Troubleshooting and Failure Analysis

## Overview

This lab investigates OSPF neighbor adjacency, route withdrawal, and connectivity recovery in a three-router Cisco IOS topology built in EVE-NG.

The exercises demonstrate how a link failure affects OSPF adjacency and routing, and how removing a LAN network advertisement can withdraw a route without necessarily breaking an existing OSPF neighbor relationship.

## Objectives

- Verify OSPF neighbor adjacency and dynamically learned routes.
- Troubleshoot OSPF adjacency loss caused by an interface shutdown.
- Restore connectivity and verify route recovery.
- Investigate route withdrawal caused by a missing OSPF network statement.
- Distinguish neighbor adjacency status from route advertisement.
- Understand failure propagation in a linear topology without an alternate path.

## Lab Environment

- **Simulator:** EVE-NG
- **Routers:** Three Cisco IOS 3725 routers
- **End devices:** Three VPCS nodes
- **Routing protocol:** OSPF
- **OSPF area:** Area 0

## Topology

<!-- Add the EVE-NG topology screenshot as topology.png in this folder. -->

![OSPF Troubleshooting Topology](topology.png)

The topology consists of three routers connected in a linear chain. VPCS01 connects to Router01, VPCS02 connects to Router02, and VPCS03 connects to Router03.

There is no alternate path between the routers, so a failure on a transit link can interrupt connectivity to remote networks.

## IP Addressing

| Device   | Interface       | IP Address     |

| Router01 | FastEthernet0/0 | 192.168.1.1/24 |
| Router01 | FastEthernet0/1 | 10.0.12.1/30   |
| Router02 | FastEthernet0/0 | 192.168.2.1/24 |
| Router02 | FastEthernet0/1 | 10.0.12.2/30   |
| Router02 | FastEthernet1/0 | 10.0.23.1/30   |
| Router03 | FastEthernet0/0 | 192.168.3.1/24 |
| Router03 | FastEthernet0/1 | 10.0.23.2/30   |
| VPCS01   |         —       | 192.168.1.10/24|
| VPCS02   |         —       | 192.168.2.10/24|
| VPCS03   |         —       | 192.168.3.10/24|

### Default Gateways

| End Device | Default Gateway |

| VPCS01     | 192.168.1.1     |
| VPCS02     | 192.168.2.1     |
| VPCS03     | 192.168.3.1     |    

## OSPF Design

| Router   | Process ID | Router ID | Area |

| Router01 |     1      | 1.1.1.1   | 0    |
| Router02 |     1      | 2.2.2.2   | 0    |
| Router03 |     3      | 3.3.3.3   | 0    |

OSPF process IDs are locally significant. They do not need to match between neighboring routers.

## Troubleshooting Scenarios

1. **Baseline verification:** Check OSPF neighbors and learned routes.
2. **Transit interface failure:** Shut down Router01 FastEthernet0/1 and observe adjacency and route changes.
3. **Interface recovery:** Restore the interface and verify that adjacency, routes, and connectivity recover.
4. **Missing LAN advertisement:** Remove Router03's OSPF network statement for 192.168.3.0/24 and observe the resulting route withdrawal.
5. **Route restoration:** Restore the network statement and verify that Router01 relearns the remote LAN.

## Verification Evidence

Command outputs and test results will be added after the evidence files have been uploaded.

- OSPF neighbor verification
- OSPF routing table verification
- Interface failure and recovery
- Route withdrawal and restoration
- End-to-end connectivity tests

## Key Learning Points

- OSPF neighbor adjacency and route advertisement are separate concepts.
- Transit interface failures can cause adjacency loss and route recalculation.
- A specific route can disappear while an OSPF neighbor remains FULL.
- Restoring the interface or network advertisement can restore routing.
- A linear topology has no alternate path to provide redundant connectivity.

## Lab Status

Troubleshooting scenarios completed. Configuration files, topology image, and verified command outputs will be documented in the following sections.
