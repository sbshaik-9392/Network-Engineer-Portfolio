# Lab 02 - Routing and Connectivity Verification

## 1. Router01 Routing Table

Command: `show ip route`

Verified routes:

| Route Type | Destination Network | Next Hop / Interface |
|---|---|---|
| Connected (C) | 10.0.0.0/30 | FastEthernet0/1 |
| Connected (C) | 192.168.1.0/24 | FastEthernet0/0 |
| Static (S) | 192.168.2.0/24 | 10.0.0.2 |

Static route configured:

`ip route 192.168.2.0 255.255.255.0 10.0.0.2`

## 2. Router02 Routing Table

Command: `show ip route`

Verified routes:

| Route Type | Destination Network | Next Hop / Interface |
|---|---|---|
| Connected (C) | 10.0.0.0/30 | FastEthernet0/1 |
| Connected (C) | 192.168.2.0/24 | FastEthernet0/0 |
| Static (S) | 192.168.1.0/24 | 10.0.0.1 |

Static route configured:

`ip route 192.168.1.0 255.255.255.0 10.0.0.1`

## 3. End-to-End Connectivity

The following successful tests were reported from the completed EVE-NG lab:

- Node3 to Router02 LAN interface: `192.168.2.1`
- Node3 to Node4: `192.168.2.10`
- Node4 to Node3: `192.168.1.10`

## 4. Interface Status

Both routers' interfaces were reported as up/up during verification.

## 5. Result

The routing tables contain the expected directly connected networks and reciprocal static routes. The reported ping tests confirm end-to-end connectivity between the two LANs.

## Evidence

Raw command outputs and terminal screenshots can be added to this directory when available.
