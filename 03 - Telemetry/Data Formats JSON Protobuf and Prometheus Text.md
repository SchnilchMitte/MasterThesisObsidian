---
title: "Data Formats - JSON, Protobuf and Prometheus Text"
tags: [serialization, telemetry]
---
# Data Formats: JSON, Protobuf and Prometheus Text

| Format | Human-readable | Schema/typing | Typical role here |
|---|---|---|---|
| JSON | Yes | loose unless external schema | APIs/debugging/candidate Kafka format |
| Protobuf | No/binary | explicit `.proto` schema | gNMI messages, GoFlow2 flow representation, candidate canonical Kafka schema |
| Prometheus text exposition | Yes | metric exposition conventions | Telegraf `/metrics` → Prometheus scrape |

## Key rule

Transport protocol and payload format are different dimensions.

Examples:
- Protobuf over gRPC over HTTP/2/TCP.
- Prometheus text over HTTP/TCP.
- Protobuf record value inside Kafka over TCP.

## Why canonical format matters

If every NDT component has to understand raw gNMI, sFlow, Junos-specific paths and GoFlow2 internals, coupling is high. A canonical event schema allows collectors/adapters to own protocol-specific translation.
