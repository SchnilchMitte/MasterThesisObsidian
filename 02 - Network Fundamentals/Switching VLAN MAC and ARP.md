---
title: "Switching, VLAN, MAC and ARP"
tags: [networking, layer2, fundamentals]
---
# Switching, VLAN, MAC and ARP

## MAC addressing and switching

Ethernet switches forward frames based on destination MAC addresses. They learn source MAC addresses on ingress ports and maintain a MAC/FDB table.

```text
Frame arrives on port 1
src MAC = A → learn A is on port 1
dst MAC = B → look up B in FDB → forward to matching port
```

Unknown/broadcast destinations can be flooded within the Layer-2 broadcast domain.

## VLAN

A VLAN logically separates Layer-2 broadcast domains. IEEE 802.1Q tags can carry VLAN identifiers between switches. Access ports typically present one untagged VLAN to an endpoint; trunk links can carry multiple VLANs.

## ARP

IPv4 ARP resolves a local IPv4 next-hop address to a MAC address.

```text
IP next hop known
     ↓ ARP
MAC address learned
     ↓
Ethernet frame sent
```

IPv6 uses Neighbor Discovery rather than ARP.

## Why relevant to the thesis

Topology and forwarding state can differ at L2 and L3. A digital twin should be explicit about whether a "link" represents physical connectivity, VLAN adjacency, IP adjacency, routing adjacency, or an SDN logical path.
