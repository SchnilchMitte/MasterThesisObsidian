---
title: "REST HTTP vs gRPC"
tags: [http, grpc, api]
---
# REST/HTTP vs gRPC

## REST-style HTTP API

Often represents resources and operations through HTTP methods/URLs and commonly exchanges JSON. Prometheus exposes HTTP APIs for querying.

## gRPC

Defines services/RPC methods and typed messages, commonly with Protobuf over HTTP/2. gNMI is a gRPC-based network-management API.

## Practical difference in this project

```text
gNMI stream:
Telegraf ↔ QFX using gRPC/HTTP2

Prometheus query:
ExperimentRunner/Grafana → Prometheus HTTP API
```

Do not describe every HTTP API as REST unless its semantics actually follow a RESTful design. "HTTP API" is the safer general term for Prometheus queries.
