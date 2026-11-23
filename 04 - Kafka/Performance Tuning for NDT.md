---
title: "Kafka Performance Tuning for NDT"
tags: [kafka, performance, evaluation]
---
# Kafka Performance Tuning for NDT

Performance is a trade-off between **latency, throughput, durability, CPU, memory, and network overhead**.

## Producer-side knobs to study

- batching / `linger.ms`
- batch size
- compression
- acknowledgements
- idempotence/retries
- producer buffer limits

A larger batch can improve throughput/network efficiency while adding wait time before send.

## Topic/broker knobs

- partition count
- replication factor
- retention policy
- segment/compaction behavior
- broker disk/network capacity

## Consumer-side knobs

- fetch sizes/wait behavior
- number of consumer instances
- processing batch size
- commit strategy
- deserialization cost
- State Builder/NDT processing cost

## NDT-specific metrics

Do not optimize only broker throughput. Measure:
- event-to-NDT apply latency,
- state age/freshness,
- consumer lag,
- event loss/gaps,
- duplicates,
- ordering violations at entity level,
- recovery time,
- bytes/sec added to underlying network,
- CPU/memory on collectors/brokers/consumers.

## Suggested experimental factors

- telemetry update rate,
- number of switches/interfaces,
- flow volume,
- partition count,
- batching,
- compression,
- broker/consumer failure,
- management vs constrained/shared transport conditions.
