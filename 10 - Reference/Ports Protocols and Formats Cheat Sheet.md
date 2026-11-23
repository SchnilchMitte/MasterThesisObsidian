---
title: "Ports Protocols and Formats Cheat Sheet"
tags: [cheatsheet, protocols]
---
# Ports, Protocols and Formats Cheat Sheet

| Item | Role | Transport / format | Project value |
|---|---|---|---|
| Ethernet | L2 framing | Ethernet | 10/100GbE fabric |
| IPv4 | L3 addressing/routing | IP | management/data ranges |
| TCP | reliable transport | TCP | gRPC, HTTP, Kafka |
| UDP | datagram transport | UDP | sFlow commonly |
| HTTP/2 | multiplexed application transport | over TCP | gRPC foundation |
| gRPC | RPC framework | HTTP/2 + Protobuf | gNMI implementation |
| gNMI | network management API | gRPC | telemetry subscription |
| YANG/OpenConfig | data model | schema/path semantics | meaning of network state |
| Protobuf | serialization/schema mechanism | binary | gNMI and GoFlow2 use cases |
| sFlow | sampled traffic telemetry | commonly UDP | flow visibility |
| Kafka | event-streaming protocol/platform | TCP | central hub |
| Prometheus exposition | metrics format | HTTP text exposition | Telegraf → Prometheus |
| PromQL/API | query language/API | HTTP | Grafana/ExperimentRunner |

## Project ports — verify

| Service | Known/likely port | Status |
|---|---:|---|
| QFX gNMI | `50051` vs `5051` | **TBD — conflicting note** |
| Telegraf Prometheus endpoint | `9126` vs possibly mistyped `91026` | **TBD** |
| Prometheus web/API | `9090` | Known from project note / typical |
| sFlow collector | often `6343/UDP` | **verify project config** |
| Kafka broker listener | often `9092/TCP` but configurable | **TBD** |

Never present a conventional/default port as the project's actual port until verified.
