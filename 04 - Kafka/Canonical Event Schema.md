---
title: "Canonical Event Schema"
tags: [kafka, schema, protobuf]
---
# Canonical Event Schema

A central hub benefits from a project-owned event envelope so downstream consumers are not tightly coupled to raw gNMI or sFlow formats.

## Proposed common envelope

```text
schema_version
message_type
event_id
source_device
source_component
entity_id
event_time_ns
collector_time_ns
producer_time_ns
experiment_id
source_protocol
source_path / origin
sequence information (if available)
payload
```

## Why multiple timestamps?

- `event_time`: when the source/device says the event occurred.
- `collector_time`: when collector received/processed it.
- `producer_time`: when handed to Kafka producer.
- Kafka record timestamp: broker/producer timestamp depending configuration.
- `ndt_apply_time`: measured by NDT when state is applied.

Then:

```text
collector delay = collector_time - event_time
broker/path delay ≈ ndt_receive_time - producer_time
E2E freshness delay = ndt_apply_time - event_time
```

Clock synchronization must be good enough for these comparisons.

## Preserve source semantics

Do not throw away useful provenance such as:
- original gNMI path,
- origin/model,
- exporter ID,
- sampling rate,
- sequence number,
- data quality flags.

## Schema technology

Protobuf is a strong candidate because the project already uses it and it supports typed evolution. The thesis should still justify the choice and schema-governance strategy rather than assume it is automatically optimal.
