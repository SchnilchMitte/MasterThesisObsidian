---
title: "Routing, RIB, FIB and Forwarding"
tags: [networking, routing, sdn]
---
# Routing, RIB, FIB and Forwarding

## RIB

The Routing Information Base contains routes learned/configured by routing protocols, static configuration, or controllers. It represents control-plane routing knowledge.

## FIB

The Forwarding Information Base contains the entries used by the data plane to make packet-forwarding decisions. The selected routing information is programmed into forwarding structures optimized for fast lookup.

## Simplified flow

```text
Routing / controller information
          ↓
         RIB
          ↓ best/selected routes
         FIB
          ↓
packet forwarding
```

## Why it matters to an NDT

A twin can be inconsistent if it knows the intended route but not the actual forwarding state. Closed-loop confirmation should distinguish:
- desired control intent,
- controller state,
- programmed device state,
- observed traffic behavior.

## SDN relation

A controller such as Ryu may influence forwarding directly through a southbound protocol. The exact project mechanism remains **TBD**.
