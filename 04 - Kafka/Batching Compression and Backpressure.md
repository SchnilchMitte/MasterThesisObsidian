---
title: "Kafka Batching, Compression and Backpressure"
tags: [kafka, performance, backpressure]
---
# Batching, Compression and Backpressure

## Batching

Producers can aggregate multiple records into larger requests. Benefits:
- fewer requests,
- better throughput,
- lower protocol overhead per record.

Cost:
- waiting to form a batch can increase latency.

## Compression

Compression can reduce network/disk bytes but costs CPU and can add processing delay. The best setting depends on event size, redundancy, CPU budget, and shared-network constraints.

## Backpressure

If downstream components process more slowly than events arrive, queues/buffers/lag grow.

Kafka makes this visible as consumer lag instead of forcing the producer to wait for each consumer. But the NDT can still become stale.

## NDT interpretation

High broker throughput with high NDT consumer lag is a failed synchronization outcome. Always evaluate the whole pipeline.
