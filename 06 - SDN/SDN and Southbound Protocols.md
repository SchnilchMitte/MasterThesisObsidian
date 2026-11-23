---
title: "SDN and Southbound Protocols"
tags: [sdn, openflow, netconf]
---
# SDN and Southbound Protocols

A southbound interface connects controller logic to network devices.

## OpenFlow

Historically central to SDN. A controller can install/query forwarding-table entries using match/action abstractions. Ryu supports multiple OpenFlow versions.

## NETCONF

Configuration-management protocol often used with YANG models. It is different from OpenFlow's flow-table-oriented model.

## gNMI Set

gNMI can also apply configuration through `Set` RPCs where the device/model supports it. That does not mean the project currently uses gNMI for control.

## gRIBI

OpenConfig defines gRIBI for programmatically modifying routing/forwarding entries. Again, this is a possible technology class, not a claim about the current testbed.

## Project rule

Do not write "Ryu controls QFX via OpenFlow" until verified. Current evidence only establishes **Ryu as the SDN controller**.

## Sources

- Ryu: https://ryu-sdn.org/
- OpenConfig RPCs: https://openconfig.net/rpc/
