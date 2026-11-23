---
title: "Project Overview"
tags: [project, overview]
---
# Project Overview

## Thesis idea

The project investigates a data infrastructure between a physical network and a **Network Digital Twin (NDT)**. The intended architecture uses **Apache Kafka as a central event/data hub** for device telemetry, flow telemetry, topology/control state, and potentially the return path for closed-loop network optimization.

## High-level goal

```text
Physical Network
      ↓ observe
Telemetry / Flow / Topology
      ↓ distribute
Kafka
      ↓ synchronize
NDT
      ↓ predict / optimize
Kafka
      ↓ validate / control
Ryu
      ↓ actuate
Physical Network
```

The thesis is therefore not simply "benchmark Kafka". The core research problem is how a messaging/event-streaming architecture influences the **freshness, reliability, consistency, reproducibility, scalability, and network overhead** of the data used by an NDT.

## Existing components

| Component              | Project role                                       | Status                                            |
| ---------------------- | -------------------------------------------------- | ------------------------------------------------- |
| Juniper QFX switches   | Physical network                                   | Known                                             |
| Junos                  | Network OS on QFX                                  | Known                                             |
| gNMI                   | Streaming telemetry interface                      | Known                                             |
| Telegraf `inputs.gnmi` | gNMI collector                                     | Known                                             |
| Prometheus             | Time-series monitoring store/query                 | Known                                             |
| Grafana                | Visualization                                      | Known                                             |
| sFlow                  | Flow/packet sampling telemetry                     | Known                                             |
| GoFlow2                | sFlow collector/normalizer                         | Known                                             |
| Kafka                  | Existing flow-data path; target central hub        | Known / Planned KLaus did a basic setup for flwos |
| Ryu                    | SDN controller                                     | Known                                             |
| Cisco TRex             | Traffic/load generator                             | Known                                             |
| ExperimentRunner       | Experiment orchestration and Prometheus querying   | Known                                             |
| NDT                    | Digital representation/model/optimization consumer | Planned / project context                         |

## Three information domains

### Device / operational state
"How is the device behaving?" / "Wie geht es dem device"

Examples: CPU, temperature, interface state, counters, errors, drops, queue metrics.

Path: [[03 - Telemetry/gNMI]] → [[03 - Telemetry/Telegraf]]

### Traffic / flow state
"What traffic is traversing the network?" / "Who is causing high traffic on Switch x" / "Who is sending Data over this Link?"

Examples: source/destination, protocol, sampled packets, bytes, interfaces. 5 Tuple

Path: [[03 - Telemetry/sFlow]] → [[03 - Telemetry/GoFlow2]]

### Control / topology state
"How is the network connected and how should it forward?"

Examples: nodes, links, paths, forwarding rules, control actions.

Path: [[06 - SDN/Ryu]] and [[06 - SDN/SDN and Southbound Protocols]]

## Key thesis concept

Kafka becomes the **decoupling boundary** between data producers and data consumers. This makes replay, multiple independent consumers, failure recovery, state reconstruction, and reproducible experiments possible — but introduces design questions around latency, partitioning, schemas, retention, resource usage, and control-loop semantics.

Related: [[04 - Kafka/Topic Architecture Proposal]], [[07 - NDT/Synchronization - Freshness Reliability Consistency]].
