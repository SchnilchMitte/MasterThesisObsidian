---
title: "Kafka Producers Consumers and Consumer Groups"
tags: [kafka, consumer]
---
# Producers, Consumers and Consumer Groups

## Producers

Collectors such as Telegraf and GoFlow2 can publish events to Kafka. A producer chooses or computes the target partition, usually via record key.

## Consumers

Consumers fetch records from partitions. Kafka uses a pull model on the consumer side.

## Consumer groups

One logical application should usually have one group ID. Within that group, partitions are divided among active consumer instances.

Example:

```text
net.telemetry.interface
  ├─ group: ndt-state
  ├─ group: monitoring-exporter
  └─ group: health-monitor
```

Each group can independently read the whole topic. Multiple instances within `ndt-state` can split partitions for scale.

## Consumer lag

Consumer lag is the distance between produced data and consumed/committed progress. It is a critical NDT health metric because rising lag directly means the NDT can be processing old state even if the network-to-Kafka path is healthy.

## Rebalancing

When consumers join/leave a group, partition assignment can change. Rebalances may temporarily pause processing. Include this in failure/recovery experiments if it is relevant to the chosen client/configuration.

## Source

- Kafka documentation/design: https://kafka.apache.org/44/design/design/
