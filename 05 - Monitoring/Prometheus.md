---
title: "Prometheus"
tags: [prometheus, monitoring]
---
# Prometheus

Prometheus is a monitoring system and time-series database/query engine.

## Data model

A sample is identified by:
- metric name,
- labels,
- timestamp,
- numeric value (or histogram type).

Example conceptually:

```text
interface_in_octets{device="SW01",interface="xe-0/0/1"} 18273645
```

## Collection model

Prometheus primarily uses a **pull/scrape model over HTTP**.

Current project path:

```text
Telegraf outputs.prometheus_client
        ↑ HTTP GET /metrics
Prometheus
```

Telegraf's Prometheus output exposes a `/metrics` endpoint that Prometheus polls.

## Query

PromQL provides time-series query/aggregation. The ExperimentRunner can query Prometheus through its HTTP API, while Grafana uses Prometheus as a data source.

## Kafka architecture implication

Prometheus is not naturally "a Kafka subscriber" by itself. A Kafka consumer/adapter can translate Kafka events into a metrics exposition path, or Telegraf can consume Kafka and expose metrics, depending architecture.

## Sources

- Overview: https://prometheus.io/docs/introduction/overview/
- HTTP API: https://prometheus.io/docs/prometheus/latest/querying/api/
- Querying: https://prometheus.io/docs/prometheus/latest/querying/basics/
