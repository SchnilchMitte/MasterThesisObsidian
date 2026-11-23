---
title: "Connectivity Matrix"
tags: [project, connectivity]
---
# Connectivity Matrix

This is the master table to fill from real configuration files.

| Source | Destination | Purpose | Protocol / Stack | Payload | Plane | Port | Status |
|---|---|---|---|---|---|---|---|
| QFX | Telegraf on NUC1 | Device telemetry | gNMI → gRPC → HTTP/2 → TCP/IP | gNMI messages, Protobuf-defined | Management likely | `50051` or `5051` **TBD** | Known path, port TBD |
| Telegraf | Prometheus | Metrics exposure | HTTP | Prometheus text exposition | Management | `9126`? **TBD** | Known path |
| Prometheus | ExperimentRunner | Query measurements | HTTP API / PromQL | JSON responses | Management | `9090` commonly | Known |
| Prometheus | Grafana | Query/visualization | HTTP API / PromQL | time-series query results | Management | `9090` commonly | Known |
| QFX | GoFlow2 | Flow telemetry | sFlow over UDP | sampled packet/counter records | **TBD** | commonly UDP `6343`, verify | Known path |
| GoFlow2 | Kafka | Flow distribution | Kafka protocol over TCP | normalized flow records, Protobuf in current path | **TBD** | broker listener TBD | Known path |
| Kafka | Consumer | Flow consumption | Kafka protocol | flow records | **TBD** | broker listener TBD | Known |
| Telegraf | Kafka | Future device telemetry distribution | Kafka protocol over TCP | canonical telemetry events | **TBD** | broker listener TBD | Planned |
| Ryu / topology service | Kafka | Topology/control state | application + Kafka protocol | nodes, links, route state | **TBD** | TBD | Planned |
| Kafka | NDT | NDT synchronization | Kafka protocol | telemetry, flows, topology/state | **TBD** | TBD | Planned |
| NDT | Kafka | Optimization intent | Kafka protocol | control intent | **TBD** | TBD | Planned |
| Kafka | Ryu adapter | Control command | Kafka protocol | validated command | **TBD** | TBD | Planned |
| Ryu | QFX | SDN control | OpenFlow / NETCONF / other **TBD** | forwarding/config changes | Control plane | TBD | Protocol must be verified |
| TRex | QFX/data network | Experiment traffic | Ethernet/IP/TCP/UDP/... | generated user/data traffic | Data | depends workload | Known |

## Rule

Do not finalize this table from assumptions. Confirm each `TBD` from config, packet capture, service files, or team documentation.
