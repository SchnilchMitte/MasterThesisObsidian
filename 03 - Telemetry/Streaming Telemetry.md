---
title: "Streaming Telemetry"
tags: [telemetry, streaming]
---
# Streaming Telemetry

Streaming telemetry is a model in which network state is delivered continuously or according to subscription behavior rather than queried one value at a time by periodic management polling.

## Current project example

```text
QFX → gNMI subscription stream → Telegraf
```

Telegraf's `inputs.gnmi` is a service input that consumes telemetry based on gNMI subscriptions.

## Why it is useful

- higher update rates than classic polling approaches,
- event/on-change delivery where supported,
- structured paths and values,
- long-lived sessions,
- lower polling orchestration overhead,
- better fit for near-real-time NDT synchronization.

## But streaming does not automatically mean fresh

Freshness can still degrade due to:
- sensor sampling interval,
- device scheduling,
- network delay,
- collector buffering,
- serialization/deserialization,
- broker batching,
- consumer lag,
- NDT processing time.

See [[07 - NDT/Synchronization - Freshness Reliability Consistency]].

## Source

- InfluxData Telegraf gNMI input: https://docs.influxdata.com/telegraf/v1/input-plugins/gnmi/
