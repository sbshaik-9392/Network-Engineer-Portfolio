# Lab 01 - Troubleshooting Notes

## Issue 1: Trunk Mode Configuration Rejected

### Observed Error

The switch rejected the command:

`switchport mode trunk`

The error indicated that the interface trunk encapsulation was set to Auto.

### Cause

The switch required an explicit trunk encapsulation setting before trunk mode could be enabled.

### Resolution

The following configuration was applied to the router-facing switch interface:

- `switchport trunk encapsulation dot1q`
- `switchport mode trunk`

### Verification

The command `show interfaces trunk` subsequently reported:

- Interface: Ethernet0/0
- Encapsulation: 802.1q
- Status: trunking
- Active VLANs: 1, 10, 20

## Final Connectivity Test

Pings between `192.168.10.10` and `192.168.20.10` succeeded in both directions.

This confirmed that the trunk and router subinterfaces were forwarding traffic between VLAN 10 and VLAN 20 in the tested topology.

## Learning

On switch platforms that support configurable trunk encapsulation, configure the required encapsulation before enabling trunk mode when the interface is set to Auto.
