---
title: "Prediction Optimization and GNNs"
tags: [ndt, gnn, optimization]
---
# Prediction, Optimization and GNNs

## Prediction

A model may estimate outcomes such as:
- delay,
- loss,
- congestion,
- utilization,
- impact of a routing change.

## Optimization

Optimization chooses an action based on current state and predicted/estimated outcomes.

Example:

```text
Current topology + traffic + telemetry
        ↓
NDT model
        ↓
Predict candidate routes
        ↓
Optimizer
        ↓
Desired path/control intent
```

## GNN

A Graph Neural Network is suitable for graph-structured network data. Nodes/links can carry features and the model can learn relationships across a topology.

It is not automatically reinforcement learning. A GNN can be a supervised predictor used by a separate optimizer.

## Thesis relevance

Model training is not necessarily part of the thesis. The important link is that model quality depends on data quality: stale topology or traffic state can dominate prediction error even if the trained model is good.
