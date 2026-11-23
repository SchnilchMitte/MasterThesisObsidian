---
title: "sFlow"
tags: [sflow, telemetry, flows]
---
# sFlow

sFlow is a telemetry technology focused on scalable visibility into network traffic and counters. Packet sampling is a key concept: on average, one packet out of N is sampled rather than exporting every packet.

## Project path

```text
QFX → sFlow → GoFlow2
```

## What a sample can tell you

Depending on the record and available packet header/metadata:
- exporter/agent,
- ingress/egress interface,
- source/destination addresses,
- L4 protocol/ports if available,
- packet/header information,
- sampling rate,
- counter samples.

## Sampling implication

sFlow is not a complete packet capture and a sampled flow view is not identical to an exact accounting of every packet. Statistical error/uncertainty matters when interpreting low-volume flows.

## Transport

sFlow export is commonly UDP-based. Because UDP does not retransmit lost datagrams, missing telemetry must be treated differently from reliable stream delivery.

## gNMI vs sFlow

- gNMI: operational/device state and structured model paths.
- sFlow: sampled traffic visibility and counters.

Both are telemetry, but they answer different questions.

## Source

- sFlow packet sampling basics: https://sflow.org/packetSamplingBasics/
