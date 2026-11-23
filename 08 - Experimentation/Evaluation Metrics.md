---
title: "Evaluation Metrics"
tags: [evaluation, metrics, thesis]
---
# Evaluation Metrics

## Synchronization metrics

- end-to-end event/apply latency,
- state age/freshness,
- percentile latencies (`p50`, `p95`, `p99`),
- update rate,
- stale-state duration.

## Reliability metrics

- missing events / sequence gaps where measurable,
- duplicate events,
- reconnect count,
- recovery time,
- dead-letter count,
- command success/failure.

## Kafka metrics

- producer send/error/retry rate,
- broker throughput,
- consumer lag,
- partition skew,
- bytes in/out,
- record size,
- replication/availability indicators.

## Resource metrics

- CPU,
- memory,
- disk I/O,
- network bytes/s,
- collector/broker/consumer utilization.

## Network-overhead metrics

- telemetry traffic volume,
- Kafka traffic volume,
- control traffic volume,
- percentage of link capacity,
- effect on user/experiment traffic.

## Closed-loop metrics

- intent-to-command delay,
- command-to-controller delay,
- controller-to-observed-effect delay,
- total loop time.

## Reproducibility

- ability to replay same recorded event stream,
- resulting state equality/difference,
- experiment configuration captured completely.
