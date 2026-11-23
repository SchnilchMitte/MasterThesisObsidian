---
title: "Kafka Retention Compaction and Replay"
tags: [kafka, retention, replay]
---
# Retention, Compaction and Replay

## Time/size retention

Event topics such as raw telemetry or flow samples are naturally retained for a configured time/size window. Consumers can replay data while it remains retained.

## Log compaction

Compaction retains at least the latest known record for each key while older superseded values become eligible for cleanup.

Ideal uses:
- latest device state,
- latest interface state,
- topology nodes/links,
- component health.

Example:

```text
Key: SW01|xe-0/0/1
UP → DOWN → UP → UP
```

A compacted state stream eventually preserves the latest relevant value, while an event-history topic preserves the transition history.

## Recommended dual-stream pattern

```text
raw event topic
     ↓
State Builder
     ↓
compacted state topic
```

The NDT can bootstrap from state topics and then follow live event topics.

## Replay for reproducibility

A retained event stream can support experiment replay, but only if enough context is preserved:
- timestamps,
- schema version,
- topology/config version,
- experiment ID,
- event ordering/key strategy,
- relevant control events.

## Source

- Kafka design/log compaction: https://kafka.apache.org/44/design/design/
