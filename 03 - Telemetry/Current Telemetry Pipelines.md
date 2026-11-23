---
title: "Current Telemetry Pipelines"
tags: [telemetry, project, pipeline]
---
# Current Telemetry Pipelines

## A — Streaming device telemetry

Known description:

```text
QFX Switch
 → gNMI over gRPC/TCP
 → Telegraf inputs.gnmi on NUC1
 → Telegraf internal metrics
 → HTTP Prometheus exposition
 → Prometheus on NUC1
 → ExperimentRunner via Prometheus HTTP API
```

Grafana queries Prometheus for visualization.

### Layered view

```text
Network semantics: YANG/OpenConfig path
Application API:   gNMI
RPC framework:     gRPC
Serialization:     Protobuf-defined gNMI messages
Application transport: HTTP/2
Transport:         TCP
Network:           IP
Link:              Ethernet
Collector:         Telegraf
Metric exposition: Prometheus text over HTTP
Storage/query:     Prometheus
Visualization:     Grafana
```

## B — Flow telemetry

```text
QFX
 → sFlow
 → GoFlow2
 → normalized flow representation
 → Protobuf
 → Kafka
 → Consumer
```

## C — Control

```text
Ryu ↔ QFX
```

Exact southbound protocol is **TBD**.

## D — Experiment stimulus

```text
Cisco TRex → data network / QFX fabric
```

TRex is not a telemetry component. It generates controlled traffic that causes observable network states.
