---
title: "Ryu"
tags: [ryu, sdn]
---
# Ryu

Ryu is a component-based SDN framework. Its documentation describes support for network-management/control protocols including OpenFlow, NETCONF and OF-Config.

## Project role

Known: Ryu is the SDN controller.

Unknown/TBD: the exact southbound protocol and application used between Ryu and the Juniper QFX switches in this testbed.

## Target Kafka integration

```text
NDT → Kafka intent → validator → Kafka command → Ryu adapter → Ryu → QFX
```

Ryu/topology information may also be published in the opposite direction:

```text
Ryu/topology service → Kafka → NDT
```

## Questions to verify

- Where does Ryu run?
- How does it discover topology?
- Which protocol reaches QFX?
- Which Ryu application owns forwarding decisions?
- Is topology dynamic or partly statically configured?
- How are command acknowledgements/errors exposed?

## Sources

- Ryu project: https://ryu-sdn.org/
- Ryu book: https://book.ryu-sdn.org/en/html/
