---
title: "NDT Synchronization - Freshness Reliability Consistency"
tags: [ndt, synchronization, evaluation]
---
# NDT Synchronization: Freshness, Reliability, Consistency

## Freshness

How old is the NDT's applied state relative to the physical event/state?

A basic metric:

```text
state_age = now - source_event_time
```

End-to-end application delay:

```text
T_e2e = ndt_apply_time - source_event_time
```

## Reliability

Questions:
- Are expected updates delivered?
- What happens during failures?
- Can data be replayed?
- Are duplicates handled?
- How quickly does the system recover?

## Consistency

The twin can temporarily combine values from different physical times. Example:
- link state from time `t2`,
- traffic flow estimate from `t1`,
- topology from `t0`.

The result may be individually valid values but an inconsistent global snapshot.

## Timeliness vs completeness

Waiting for all sources can improve snapshot completeness but increase latency. Applying immediately improves freshness but may expose partial/asynchronous state. This is a fundamental NDT design trade-off.

## Reproducibility

A replayable event log helps reproduce an observed NDT input sequence, provided timestamps, schemas, topology/config versions, and experiment metadata are preserved.
