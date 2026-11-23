---
title: "Network Digital Twin Fundamentals"
tags: [ndt, digital-twin]
---
# Network Digital Twin Fundamentals

A Network Digital Twin is a digital representation of a physical network that maintains sufficiently synchronized state to support observation, analysis, prediction, experimentation, or optimization.

## It is not automatically a GNN

The NDT is the broader system. It may contain:
- topology/state representation,
- telemetry ingestion,
- simulation/model components,
- ML/GNN models,
- optimization logic,
- APIs/control integration.

A GNN can be one predictive model *inside* the NDT.

## Core relationship

```text
Physical network ↔ synchronization/data infrastructure ↔ NDT
```

The quality of the twin depends not only on model accuracy but also on the freshness, completeness and consistency of the input state.

## Typical NDT state

- devices/components,
- topology/links,
- configuration/forwarding,
- telemetry metrics,
- traffic demands/flows,
- timestamps and state provenance.

## Thesis focus

The data infrastructure is part of the NDT trust boundary: stale or missing input can make a theoretically strong model produce poor predictions.
