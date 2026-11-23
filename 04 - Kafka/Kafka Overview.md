---
title: "Apache Kafka Overview"
tags: [kafka, messaging]
---
# Apache Kafka Overview

Kafka is a distributed event-streaming platform. For this thesis, think of Kafka as a durable **append-only event log plus publish/subscribe distribution layer**.

## Core entities

- **Producer** — publishes records.
- **Broker** — Kafka server storing partitions.
- **Topic** — named event stream/category.
- **Partition** — ordered append-only log within a topic.
- **Offset** — position of a record inside a partition.
- **Consumer** — fetches records.
- **Consumer group** — coordinates multiple consumers for one logical subscriber.
- **Key** — commonly determines partition and therefore ordering locality.

## Why Kafka fits the project

- decouples collectors from consumers,
- supports multiple independent subscribers,
- retains events after consumption,
- supports replay by resetting/rewinding consumer position,
- partitions for throughput and scaling,
- supports replication/fault tolerance,
- log compaction can retain latest keyed state.

## Important limitation

Kafka guarantees ordering **within a partition**, not across all partitions. Therefore topic key design is part of the NDT consistency design.

## Source

- Apache Kafka documentation: https://kafka.apache.org/documentation/
- Kafka design: https://kafka.apache.org/44/design/design/
