# Lab 01 - Verification Results

## 1. IP Addressing

| Device | IP Address | Subnet Mask | Default Gateway | VLAN |
|---|---|---|---|---|
| VPCS3 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 | 10 |
| VPCS4 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 | 20 |

## 2. Router Subinterfaces

The router is configured for Router-on-a-Stick inter-VLAN routing.

| Interface | VLAN | IP Address |
|---|---|---|
| FastEthernet0/0.10 | 10 | 192.168.10.1/24 |
| FastEthernet0/0.20 | 20 | 192.168.20.1/24 |

## 3. Switch Verification

- VLAN 10 (Servers): Ethernet0/1
- VLAN 20 (Users): Ethernet0/2
- Trunk port: Ethernet0/0
- Trunk encapsulation: IEEE 802.1Q
- Allowed and active VLANs: 1, 10, 20

## 4. Connectivity Tests

| Source | Destination | Result |
|---|---|---|
| VPCS3 | 192.168.10.10 | Successful |
| VPCS3 | 192.168.20.10 | Successful |
| VPCS4 | 192.168.20.10 | Successful |
| VPCS4 | 192.168.10.10 | Successful |

## 5. Result

Bidirectional connectivity between VLAN 10 and VLAN 20 was verified successfully using ICMP ping tests.

Inter-VLAN communication is enabled through the router subinterfaces and the 802.1Q trunk between the switch and router.

## Evidence

The configuration and verification details are based on the actual EVE-NG lab outputs. Dedicated screenshots of verification commands can be added here.
