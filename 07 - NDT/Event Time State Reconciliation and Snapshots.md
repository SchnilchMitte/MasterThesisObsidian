---
title: "Event Time, State Reconciliation and Snapshots"
tags: [ndt, state, event-time]
---
# Event Time, State Reconciliation and Snapshots

## Event time vs processing time

- **event time** — source says state/event occurred at time T.
- **processing time** — collector/broker/consumer processes it later.

For a twin, event time is crucial because two fast-arriving values may describe different physical times.

## State reconciliation

A State Builder may apply rules such as:
- ignore older version/timestamp for same entity,
- detect gaps,
- mark stale entities,
- combine multiple source streams,
- invalidate dependent state after topology changes.

## Snapshot vs stream

### Snapshot
Useful for initial bootstrap: "what is the latest known state?"

### Event stream
Useful for live updates, audit, replay, and reconstructing transitions.

Recommended architecture:

```text
retained event stream → State Builder → compacted current-state stream
```

This avoids forcing a restarting NDT to replay the entire history before becoming useful.
