---
title: "Junos Telemetry"
tags: [juniper, junos, telemetry]
---
# Junos Telemetry

Junos is the network operating system running on Juniper devices such as the QFX family. "Junos Telemetry" is best understood as the Junos capability to expose operational/network state, not as a synonym for a single transport protocol.

## In this project

The shorthand:

```text
Junos Telemetry → Prometheus → Grafana
```

is more completely represented as:

```text
QFX/Junos telemetry
   ↓ gNMI
Telegraf
   ↓ Prometheus exposition
Prometheus
   ↓ query
Grafana
```

## Typical data classes

Depending on supported paths/models:
- system/component status,
- CPU/memory/temperature,
- interfaces and counters,
- errors/discards,
- routing/protocol state,
- QoS/queues.

The exact set must be documented from the real Telegraf subscription configuration rather than assumed.
