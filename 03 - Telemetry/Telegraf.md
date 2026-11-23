---
title: "Telegraf"
tags: [telegraf, telemetry]
---
# Telegraf

Telegraf is a plugin-driven agent for collecting, processing, aggregating, and writing metrics/events.

## Generic pipeline

```text
Input plugin
   ↓
Internal Telegraf metric
   ↓ processors/aggregators (optional)
Output plugin
   ↓
Destination
```

## Current use

```text
QFX → gNMI → inputs.gnmi → Telegraf
                           ↓
                 internal metric
                           ↓
              outputs.prometheus_client
                           ↓
                     /metrics HTTP
```

For a gNMI subscription, Telegraf documents that each leaf in a `SubscribeResponse` update becomes a field and path-element keys can become tags.

## Planned Kafka use

Telegraf has an `outputs.kafka` plugin and can act as a Kafka producer.

```text
inputs.gnmi
    ↓
Telegraf metric
    ↓
serializer / canonical mapping
    ↓
outputs.kafka
    ↓
Kafka
```

Important: the output format does not have to equal the input format. Receiving gNMI/Protobuf does not mean Telegraf must emit the original gNMI Protobuf bytes.

## Thesis questions

- preserve original source timestamp?
- preserve source path/origin?
- one event per leaf or grouped message?
- how much collector buffering exists?
- what happens on Kafka outage?
- how are retries/buffers configured?

## Sources

- Telegraf overview: https://docs.influxdata.com/telegraf/v1/
- gNMI input: https://docs.influxdata.com/telegraf/v1/input-plugins/gnmi/
- Kafka output: https://docs.influxdata.com/telegraf/v1/output-plugins/kafka/
- Prometheus output: https://docs.influxdata.com/telegraf/v1/output-plugins/prometheus_client/
