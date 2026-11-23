---
title: "Network Performance Metrics"
tags: [networking, metrics, evaluation]
---
# Network Performance Metrics

## Throughput
Actual useful data delivered per unit time.

## Offered load
Traffic presented to the network. TRex can control this independently of achieved throughput.

## Bandwidth / link capacity
Maximum nominal transmission capacity of a link, e.g. 10 Gb/s or 100 Gb/s.

## Latency
Time from one measurement boundary to another. Always define start/end points.

## Jitter
Variation in packet/message latency.

## Packet loss
Packets sent but not observed/received at the expected endpoint.

## Message/event loss
Telemetry/Kafka events expected but not processed. Do not automatically equate packet loss and event loss.

## Utilization
Fraction of a resource capacity currently used.

## Good thesis practice

Use percentiles for latency distributions, not only averages:
- p50 — median,
- p95,
- p99,
- maximum where meaningful.

Always label whether a latency is:
- device → collector,
- collector → Kafka,
- Kafka → NDT,
- full end-to-end,
- closed-loop.
