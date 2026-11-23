---
title: "NDT State Model"
tags: [ndt, state]
---
# NDT State Model

A useful NDT state can be split into several layers.

## Structural state

- nodes/devices,
- ports/interfaces,
- links,
- capacities,
- topology relationships.

## Operational state

- link/interface up/down,
- counters,
- CPU/temperature,
- queues/drops/errors.

## Traffic state

- flow/traffic demand estimates,
- source/destination relationships,
- observed load.

## Control state

- active route/forwarding decisions,
- intended state,
- controller state.

## Quality/provenance state

Every value should ideally carry or be associated with:
- source,
- event time,
- receive/apply time,
- schema version,
- confidence/quality,
- staleness.

## Key insight

The NDT needs more than values. It needs to know **how trustworthy and how old those values are**.
