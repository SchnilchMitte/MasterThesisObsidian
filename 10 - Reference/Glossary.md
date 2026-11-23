---
title: "Glossary"
tags: [glossary, reference]
---
# Glossary

**Broker** — Kafka server storing and serving topic partitions.

**Canonical schema** — project-owned normalized event representation independent of raw source protocol.

**Collector** — component receiving/decoding telemetry, e.g. Telegraf or GoFlow2.

**Consumer** — application reading Kafka records.

**Consumer group** — one logical Kafka subscriber possibly implemented by multiple consumer instances.

**Control plane** — logic that determines/configures forwarding behavior.

**Data plane** — packet-forwarding path carrying traffic.

**Event time** — time at which an event occurred at/near the source.

**Flow telemetry** — traffic-focused observations such as sampled packet/flow information.

**Freshness / state age** — how old the twin's current state is relative to its source event/state.

**gNMI** — gRPC Network Management Interface used for Get/Set/Subscribe network management operations.

**gRPC** — RPC framework using HTTP/2, commonly with Protobuf.

**GoFlow2** — collector/normalizer for sFlow/NetFlow/IPFIX.

**Grafana** — dashboard/visualization system querying data sources such as Prometheus.

**Junos** — Juniper network operating system.

**Kafka** — distributed event-streaming platform used as proposed central hub.

**Key (Kafka)** — record key used by the partitioner and for keyed semantics/compaction.

**Log compaction** — Kafka cleanup mode retaining at least latest keyed state.

**Management plane** — administrative/management connectivity and services.

**NDT** — Network Digital Twin.

**Offset** — record position in a Kafka partition.

**OpenConfig** — vendor-neutral network data models and related APIs.

**Partition** — ordered Kafka log shard.

**Prometheus** — monitoring/time-series system using primarily HTTP scraping and PromQL.

**Protobuf** — Protocol Buffers, typed binary serialization mechanism.

**Producer** — application writing Kafka records.

**Replay** — re-consuming retained Kafka events from earlier offsets.

**Ryu** — SDN framework/controller used in the testbed.

**sFlow** — sampled network traffic/counter telemetry technology.

**SDN** — Software Defined Networking.

**Streaming telemetry** — continuous/subscription-oriented delivery of network state.

**Telegraf** — plugin-based collection/processing/output agent used as gNMI collector.

**TRex** — traffic generator used to create controlled network load.

**YANG** — data-modeling language for configuration/operational network state.
