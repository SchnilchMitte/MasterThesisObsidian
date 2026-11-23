---
title: "Software Defined Networking Fundamentals"
tags: [sdn, networking]
---
# Software Defined Networking Fundamentals

Software Defined Networking (SDN) separates network-control logic from packet-forwarding behavior more explicitly than traditional distributed control.

## Conceptual split

```text
Applications / optimization
        ↓
SDN controller
        ↓ southbound interface
Switch forwarding plane
```

## Why it matters to the NDT

Telemetry closes the **observation path**. SDN provides an **actuation path**. Together they enable closed-loop operation:

```text
observe → model → optimize → control → observe
```

## Important distinction

Kafka does not replace Ryu. Kafka transports events/commands; the SDN controller translates policy/control logic into network-device operations.
