---
title: "Experiment Scenarios"
tags: [evaluation, experiment]
---
# Experiment Scenarios

## Baseline

Low network load, all components healthy, dedicated management network.

Purpose: establish best-case latency and resource baseline.

## Increasing traffic load

Use TRex to increase data-plane load.

Measure whether telemetry/NDT synchronization changes despite management-network separation.

## Increasing telemetry volume

Increase:
- number of subscribed paths,
- sample/update frequency,
- active interfaces/devices,
- flow/sample rate.

Measure scalability and Kafka/consumer effects.

## Shared/constrained infrastructure approximation

If feasible, create controlled bandwidth/latency/loss constraints representing a less isolated deployment.

## Collector failure

Stop/restart Telegraf or GoFlow2. Measure stale state and recovery.

## Kafka disruption

Broker/client disconnect/failure according to safe test design. Measure buffering, retries, replay, and consumer catch-up.

## Slow consumer

Artificially slow NDT consumer. Observe lag and health detection.

## Control-loop scenario

Cause congestion → NDT observes → optimization generates intent → control path applies change → telemetry confirms effect.
