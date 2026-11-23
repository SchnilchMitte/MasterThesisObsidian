---
title: "YANG and OpenConfig"
tags: [telemetry, yang, openconfig]
---
# YANG and OpenConfig

## YANG

YANG is a data-modeling language used to describe configuration and operational state in a hierarchical schema. It defines concepts such as containers, lists, leaves, types, constraints, and paths.

YANG is **not** the transport protocol and **not** the serialization format of a gNMI RPC.

## OpenConfig

OpenConfig publishes vendor-neutral YANG models. They define reusable schema paths for interfaces, components, network instances, QoS, and other network concepts.

Example conceptually:

```text
/interfaces/interface[name=xe-0/0/1]/state/counters/in-octets
```

This path identifies the semantic network data item.

## Who needs the models?

### Network device
The QFX/Junos implementation must support the relevant schema or vendor model and map internal device state to it.

### gNMI client / Telegraf
The client needs to know the paths/origins it wants to subscribe to. It does not necessarily need every `.yang` file locally for normal path-based subscriptions. Telegraf can optionally load YANG models for certain decoding use cases.

### Prometheus / Kafka / Grafana
These systems do not inherently require YANG. Once the collector transforms the telemetry into a canonical metric/event, YANG may only survive as metadata such as `source_path` or `origin`.

## YANG vs Protobuf

| YANG | Protobuf |
|---|---|
| Defines network data model/semantics | Defines typed serialized message structures |
| Example: interface counter path | Example: gNMI `Notification` / `Update` message |
| Schema for configuration/state | General serialization/IDL mechanism |
| Network-management domain | General-purpose |

## Sources

- OpenConfig models/projects: https://openconfig.net/projects/
- OpenConfig docs: https://openconfig.net/docs/
- Telegraf gNMI input: https://docs.influxdata.com/telegraf/v1/input-plugins/gnmi/
