---
title: "Kafka and Pipeline Failure Scenarios"
tags: [failure, kafka, evaluation]
---
# Failure Scenarios

## Collector failure

Effect: source keeps changing while no events are published.

Detect via heartbeat/last-update age and collector health.

## Network path failure

Effect: gNMI disconnect, sFlow loss, Kafka connectivity loss.

Measure reconnect/recovery and state staleness.

## Kafka broker failure

Effect depends on replication, leader election and client configuration. Measure unavailable interval and producer/consumer recovery.

## Slow NDT consumer

Kafka remains healthy but consumer lag grows. NDT state becomes stale.

## Bad/unknown schema

Consumer cannot decode event. Route to dead-letter handling and surface schema mismatch as health problem.

## Duplicate/replayed event

Consumer must handle duplicate processing safely, especially on control path.

## Out-of-order domain state

Can occur when related data is spread across partitions or different source pipelines. Use entity keys, event times, versions, and reconciliation rules.

## Ryu/control failure

Command can be accepted by Kafka but never reach device. Separate messaging success from controller success and physical-state confirmation.

## Clock drift

Can make measured latency/freshness misleading. Clock quality is part of the experiment infrastructure.
