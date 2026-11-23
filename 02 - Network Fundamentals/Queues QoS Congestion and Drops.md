---
title: "Queues, QoS, Congestion and Drops"
tags: [networking, qos, congestion]
---
# Queues, QoS, Congestion and Drops

## Why queues exist

Packets can arrive faster than an egress interface can transmit them. The switch buffers packets in queues until they can be sent.

## Congestion

When sustained offered traffic exceeds available output capacity, queue occupancy grows. If buffers/policies cannot accept more packets, drops occur.

## QoS concepts

- classification — identify traffic class,
- marking — encode priority/class information,
- queuing — separate traffic into queues,
- scheduling — choose which queue transmits next,
- shaping — limit transmission rate smoothly,
- policing — enforce a traffic-rate policy, often by dropping/remarking.

## Telemetry relevance

Useful indicators:
- interface utilization,
- queue occupancy,
- dropped/discarded packets,
- error counters,
- latency/jitter,
- traffic-class utilization.

## NDT relevance

A model predicting congestion needs both network structure/capacity and current traffic/load. gNMI can expose operational counters/queue state while flow telemetry helps estimate traffic demands.
