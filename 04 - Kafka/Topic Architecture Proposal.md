---
title: "Kafka Topic Architecture Proposal"
tags: [kafka, topic-design, project]
---
# Kafka Topic Architecture Proposal

| Topic | Purpose | Producer | Recommended key | Cleanup | Typical consumers |
|---|---|---|---|---|---|
| `net.telemetry.device.v1` | CPU, memory, temperature, hardware state | Telegraf | `device_id` | delete/time | NDT, monitoring, health |
| `net.telemetry.interface.v1` | interface state/counters/errors/drops | Telegraf | `device_id|interface_id` | delete/time | NDT, State Builder, monitoring |
| `net.flow.sample.v1` | normalized sFlow/flow records | GoFlow2 | `flow_hash` or chosen exporter-flow key | delete/time | NDT, traffic analysis |
| `net.topology.node.v1` | node lifecycle/state | topology service/Ryu adapter | `device_id` | compact | NDT |
| `net.topology.link.v1` | link lifecycle/properties | topology service/Ryu adapter | canonical link ID | compact | NDT |
| `net.state.device.v1` | current consolidated device state | State Builder | `device_id` | compact | NDT bootstrap |
| `net.state.interface.v1` | current consolidated interface state | State Builder | `device_id|interface_id` | compact | NDT bootstrap |
| `net.control.intent.v1` | high-level desired change from NDT | NDT | target / intent ID | delete/time | validator/control service |
| `net.control.command.v1` | validated executable command | control service | `target_device` | delete/time | Ryu adapter |
| `net.control.result.v1` | accepted/applied/failed/rejected result | Ryu adapter | `command_id` | delete/time | NDT, monitoring |
| `net.health.v1` | component/pipeline health | health service | `component_id` | compact | NDT, Grafana/monitoring |
| `net.experiment.v1` | run metadata, start/stop/scenario | ExperimentRunner | `experiment_id` | long retention | evaluation/replay |
| `net.deadletter.v1` | records that could not be parsed/processed | processors/consumers | event/error ID | delete/time | debugging |

## Naming convention

Recommended structure:

`<domain>.<class>.<entity>.<version>`

Avoid embedding switch IDs in topic names. Use record keys and payload fields instead.

## Performance principle

Do not create a separate topic for every metric. Topic boundaries should reflect different semantics, retention, security, throughput, ordering or consumer requirements.
