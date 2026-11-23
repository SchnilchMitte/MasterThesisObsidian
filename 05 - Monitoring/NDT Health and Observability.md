---
title: "NDT Health and Observability"
tags: [health, ndt, monitoring]
---
# NDT Health and Observability

A trustworthy NDT should expose not only network state but also the **quality of its knowledge**.

## Health dimensions

### Physical-network health
- device reachability,
- link state,
- errors/drops,
- resource saturation.

### Telemetry health
- gNMI session connected,
- last update age,
- expected vs received update rate,
- sFlow sequence/gap indicators where available,
- collector errors.

### Kafka health
- producer failures/retries,
- broker availability,
- consumer lag,
- dead-letter events,
- partition imbalance.

### NDT health
- state age,
- missing entities,
- topology consistency,
- prediction error,
- model/input validity.

### Control-loop health
- pending commands,
- command age,
- rejected/failed controls,
- time until physical effect observed.

## Example traffic-light logic

- **Green**: fresh telemetry, low lag, all key devices reachable.
- **Yellow**: state age increasing or partial data missing.
- **Red**: critical source disconnected, lag above threshold, control failure, or state no longer trustworthy.

The thesis can investigate whether telemetry and infrastructure metrics allow distinguishing a network failure from a telemetry-pipeline failure or NDT/model anomaly.
