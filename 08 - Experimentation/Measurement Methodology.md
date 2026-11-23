---
title: "Measurement Methodology"
tags: [evaluation, methodology]
---
# Measurement Methodology

## Define measurement boundaries

Every metric should answer:
- start timestamp generated where?
- end timestamp generated where?
- same clock or synchronized clocks?
- warm-up excluded?
- how many repetitions?

## Latency distribution

Report at least central tendency plus tail behavior. For event pipelines, p95/p99 often expose batching, GC, I/O or recovery effects hidden by averages.

## Controlled variables

Keep fixed where possible:
- software versions,
- Kafka configuration,
- topology,
- subscription paths/rates,
- TRex profile,
- hardware allocation,
- clock synchronization.

## Independent variables

Examples:
- telemetry volume,
- traffic load,
- partition count,
- batching/compression,
- failure condition,
- network constraint.

## Dependent variables

- NDT state freshness,
- latency,
- consumer lag,
- CPU/memory/network overhead,
- recovery time,
- errors/loss/duplicates.

## Repetition and reproducibility

Use stable experiment IDs and preserve run configuration with results. Avoid drawing strong conclusions from one run.
