---
title: "Quick Mental Model"
tags: [cheatsheet, project]
---
# Quick Mental Model

## One-line definitions

- **QFX** — the real switch.
- **Junos** — operating system on the switch.
- **YANG/OpenConfig** — what network state/configuration means and how it is structured.
- **gNMI** — API used to get/set/subscribe to network state.
- **gRPC** — RPC framework carrying gNMI operations.
- **Protobuf** — typed binary message/schema mechanism used by gNMI and elsewhere.
- **Telegraf** — decodes/normalizes gNMI into metrics and outputs them elsewhere.
- **sFlow** — sampled traffic telemetry.
- **GoFlow2** — decodes/normalizes flow telemetry.
- **Kafka** — durable event backbone between producers and consumers.
- **Prometheus** — stores/queries numerical time series.
- **Grafana** — visualizes queried data.
- **Ryu** — SDN controller that can actuate network behavior.
- **TRex** — generates controlled traffic/load.
- **NDT** — digital representation/model consuming state and potentially producing optimization decisions.

## Three arrows to remember

```text
OBSERVE:
QFX → gNMI/sFlow → collectors → Kafka → NDT

MONITOR:
Kafka/collectors → Prometheus → Grafana

CONTROL:
NDT → Kafka → validation/Ryu → QFX
```

## One sentence thesis mental model

The thesis studies whether a centralized event-streaming data layer can provide the NDT with sufficiently fresh, reliable and reproducible network state — and how that architecture behaves when load, failures, scaling and deployment conditions become less ideal.
