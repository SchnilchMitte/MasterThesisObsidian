---
title: "Protocol Buffers"
tags: [protobuf, serialization]
---
# Protocol Buffers

Protocol Buffers (Protobuf) is a language-neutral, platform-neutral mechanism for serializing structured typed data.

## Schema example

```proto
message InterfaceMetric {
  string device_id = 1;
  string interface_id = 2;
  string metric = 3;
  uint64 value = 4;
  int64 event_time_ns = 5;
}
```

The `.proto` file defines field names, types and numeric field identifiers. Generated bindings allow applications to serialize/deserialize the binary representation.

## Why use it?

- compact binary representation,
- efficient parsing,
- explicit typed schema,
- cross-language code generation,
- backward/forward-compatible evolution when field-number rules are respected.

## Two different Protobuf uses in this project

### gNMI
The gNMI service and messages such as notifications/updates are defined via Protobuf.

### GoFlow2 → Kafka
GoFlow2 can normalize flow protocols into its own Protobuf representation.

These are **not the same schema** just because both use Protobuf.

## Key distinction

```text
YANG: What does a network value mean and where is it in the model?
Protobuf: How is a typed application message represented and serialized?
```

## Schema evolution rule of thumb

Never reuse an old field number for a different meaning. Add new fields with new numbers and preserve compatibility rules.

## Source

- Protobuf overview: https://protobuf.dev/overview/
