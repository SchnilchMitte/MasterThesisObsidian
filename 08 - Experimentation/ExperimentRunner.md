---
title: "ExperimentRunner"
tags: [experiment, project]
---
# ExperimentRunner

The ExperimentRunner is part of the existing test infrastructure.

Known behavior:
- can generate/coordinate defined network load,
- queries Prometheus through its HTTP API for measurements corresponding to an experiment window.

## Conceptual run

```text
1. create experiment_id
2. record configuration/topology version
3. start traffic profile
4. record t_start
5. collect telemetry / Kafka events
6. inject optional failure/change
7. stop traffic
8. record t_end
9. query Prometheus / collect Kafka metrics
10. persist results + metadata
```

## Recommended extension for thesis

Ensure every Kafka event can be associated with an `experiment_id` where practical. Record producer/broker/consumer configuration so a run is reproducible.
