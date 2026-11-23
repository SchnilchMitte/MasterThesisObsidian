---
title: "Time Synchronization, NTP and PTP"
tags: [time, evaluation, networking]
---
# Time Synchronization, NTP and PTP

Timestamp-based latency measurements are only valid if clocks are sufficiently synchronized.

## NTP

Network Time Protocol synchronizes clocks over packet networks and is common for general server/network-device time synchronization.

## PTP

Precision Time Protocol is designed for higher-precision clock synchronization and can use hardware timestamping in suitable networks.

## Thesis issue

If QFX and NDT clocks differ by 20 ms, a measured 5 ms telemetry latency based on their timestamps is meaningless.

## Recommended practice

Record:
- synchronization mechanism,
- clock source,
- measured/estimated clock offset,
- timestamp resolution,
- whether timestamp is generated at source, collector, producer, broker, or consumer.

Where clocks cannot be trusted, also measure local segment latencies using monotonic clocks within the same host/process boundary.
