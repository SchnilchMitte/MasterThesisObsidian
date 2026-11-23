---
title: "Grafana"
tags: [grafana, monitoring]
---
# Grafana

Grafana is a visualization/dashboard and exploratory query layer over data sources such as Prometheus.

## Project path

```text
Prometheus → Grafana
```

Grafana is not the collector for QFX telemetry. It queries a data source that stores/exposes the data.

## Suitable thesis dashboards

- end-to-end telemetry latency,
- NDT state age,
- Kafka consumer lag,
- broker/collector health,
- telemetry rate,
- message errors/drops,
- switch CPU/interface load,
- TRex offered traffic,
- command result/closed-loop state.

## Source

- Grafana data sources: https://grafana.com/docs/grafana/latest/datasources/
