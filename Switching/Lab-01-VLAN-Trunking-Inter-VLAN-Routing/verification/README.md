# Lab 01 - Verification Results

## 1. VLAN Verification

Command: `show vlan brief`

- VLAN 10 — Servers — Ethernet0/1
- VLAN 20 — Users — Ethernet0/2

## 2. Trunk Verification

Command: `show interfaces trunk`

- Trunk interface: Ethernet0/0
- Encapsulation: 802.1Q
- Operational status: trunking
- Active VLANs: 1, 10, 20

## 3. IP Addressing

| Device | IP Address | Default Gateway |
|---|---|---|
| VPCS3 (VLAN 10) | 192.168.10.10/24 | 192.168.10.1 |
| VPCS4 (VLAN 20) | 192.168.20.10/24 | 192.168.20.1 |

## 4. Ping Verification

**Test 1:** VPCS3 to VPCS4

Source: `192.168.10.10`

Destination: `192.168.20.10`

Result: Successful replies received for all 5 displayed ICMP sequences.

**Test 2:** VPCS4 to VPCS3

Source: `192.168.20.10`

Destination: `192.168.10.10`

Result: Successful replies received for all 5 displayed ICMP sequences.

## Conclusion

The supplied test outputs confirm successful connectivity between VLAN 10 and VLAN 20 through Router-on-a-Stick inter-VLAN routing in the EVE-NG lab.
