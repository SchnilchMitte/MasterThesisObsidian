---
title: "Research Questions"
tags: [thesis, research-question]
---
# Research Questions

## Current direction

### RQ1 — synchronization

How effectively can an event-driven telemetry architecture maintain timely, reliable, and consistent synchronization between a physical network and its NDT under varying loads and failure conditions?

### RQ2 — infrastructure and scaling effect

A strong concise formulation is:

**What effect do infrastructure characteristics and increasing telemetry volume have on NDT synchronization and the underlying network as the system scales?**

This deliberately remains broader than only "management vs production network" while allowing that scenario in the evaluation.

### RQ3 — health

To what extent can telemetry and infrastructure metrics be used to assess NDT health and distinguish between network, telemetry-pipeline, and NDT-related issues?

## Evaluation mapping

| RQ | Main measures |
|---|---|
| RQ1 | latency/freshness, reliability, consistency, recovery |
| RQ2 | telemetry volume, network overhead, resource usage, synchronization under scale |
| RQ3 | state age, connectivity, consumer lag, missing data, component failures, prediction/behavior indicators |

## Non-goal

The thesis does not need to benchmark every messaging product exhaustively. Candidate systems can be assessed from literature/documentation/architecture/operational suitability, followed by implementation/evaluation of the chosen approach.
