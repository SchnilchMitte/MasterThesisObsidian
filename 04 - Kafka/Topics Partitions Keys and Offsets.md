---
title: "Kafka Topics Partitions Keys and Offsets"
tags: [kafka, partitioning]
---
# Topics, Partitions, Keys and Offsets

## Topic

Logical event stream such as:
- `net.telemetry.interface.v1`
- `net.flow.sample.v1`
- `net.control.command.v1`

## Partition

Each partition is an ordered append-only log. More partitions allow parallel production/consumption but make global ordering impossible without extra logic.

## Key

Records with the same key are normally routed to the same partition. This is the primary mechanism to keep related events ordered.

Recommended examples:

| Topic class | Key |
|---|---|
| device telemetry | `device_id` |
| interface telemetry | `device_id|interface_id` |
| topology node | `device_id` |
| topology link | canonical `endpointA|endpointB` |
| flow | `flow_hash` or exporter/flow strategy |
| control command | `target_device` |
| control result | `command_id` or target depending processing need |

## Offset

A monotonically increasing position per partition. Consumers track where they are. Repositioning the offset enables replay.

## Thesis trade-off

Too few partitions → limited parallelism/hot partitions.

Too many partitions → greater operational overhead and harder cross-partition reasoning.

The number should be justified experimentally rather than chosen only from generic best practices.
