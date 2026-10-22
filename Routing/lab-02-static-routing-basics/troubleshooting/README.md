# Lab 02 - Static Routing Troubleshooting

## 1. Troubleshooting Checklist

Use the following checks if end-to-end connectivity fails between the two LANs.

### Check 1: Interface Status

Run on both routers:

```text
show ip interface brief
```

- Confirm the required interfaces are up/up.
- Check the interface IP addresses and subnet masks.
- If an interface is down, investigate the physical or virtual link and interface configuration.

### Check 2: Routing Table

Run:

```text
show ip route
```

- Confirm both directly connected LANs and the inter-router network appear as connected routes.
- Confirm the remote LAN appears as a static route.

### Check 3: Static Route Configuration

**Router01:**

```text
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

**Router02:**

```text
ip route 192.168.1.0 255.255.255.0 10.0.0.1
```

- Verify the destination network and next-hop IP.
- Ensure each router has a route back to the opposite LAN.

### Check 4: Next-Hop Reachability

From Router01, test:

```text
ping 10.0.0.2
```

From Router02, test:

```text
ping 10.0.0.1
```

These tests help verify connectivity across the inter-router link.

### Check 5: End-Device Configuration

On Node3 and Node4, verify:

- IP address and subnet mask.
- Default gateway.
- Reachability of the local router's LAN interface.

### Check 6: End-to-End Ping

Test connectivity in this order:

1. End device to its local gateway.
2. Router to the remote router's LAN interface.
3. Node3 to Node4.
4. Node4 to Node3.

This sequence helps identify where connectivity stops.

## 2. Packet Flow and TTL

- A router checks its routing table to select the next hop.
- The IP packet's TTL decreases as it passes through each router.
- If the TTL reaches zero, the packet is discarded.
- Use traceroute where supported to help identify the path taken by packets.

## 3. Lab Observation

The lab's reported verification showed the expected static routes and successful pings between the two LANs. No specific connectivity failure was documented during the completed lab.

## 4. Key Learning

Successful static routing requires correct interface addressing, a valid next hop, a route to the remote network, and a return route. End-to-end testing confirms whether both LANs can communicate.
