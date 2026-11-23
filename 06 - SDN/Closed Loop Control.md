---
title: "Closed Loop Control"
tags: [closed-loop, sdn, ndt]
---
# Closed Loop Control

## Loop stages

1. **Observe** physical state via gNMI/sFlow/topology.
2. **Distribute** events through Kafka.
3. **Synchronize** NDT state.
4. **Predict/optimize** candidate network action.
5. **Validate** action against policy/safety/current state.
6. **Actuate** through Ryu/controller.
7. **Observe effect** through new telemetry.
8. **Confirm/reconcile** desired vs actual state.

## Why confirmation matters

There are multiple truths:
- command published,
- command consumed,
- controller accepted it,
- device accepted it,
- network converged,
- telemetry observed the new state.

Only the final stages demonstrate physical effect.

## Control-loop latency

```text
T_loop = T_observe + T_distribute + T_ndt + T_optimize + T_control + T_converge + T_reobserve
```

The thesis can measure only some components initially, but should define boundaries explicitly.
