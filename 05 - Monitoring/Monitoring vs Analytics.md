---
title: "Monitoring vs Analytics"
tags: [monitoring, analytics]
---
# Monitoring vs Analytics

## Monitoring

Answers questions such as:
- What is the current value?
- Is it within a threshold?
- How did it change over time?
- Is the component up?

Typical stack: Prometheus + Grafana.

## Analytics

Applies additional reasoning/processing:
- anomaly detection,
- root-cause analysis,
- traffic classification,
- capacity planning,
- prediction,
- feature extraction.

The current project does **not require a separate Analytics component** merely because a diagram can contain one. If no concrete service exists, omit it from the architecture.

## NDT overlap

Some analytics may live inside the NDT. The boundary is architectural, not semantic: the NDT can itself contain predictive models and optimization logic.
