---
title: "gRPC"
tags: [grpc, telemetry]
---
# gRPC

gRPC is a remote-procedure-call framework. Services and messages are typically described using Protobuf definitions and transported using HTTP/2.

## Why gRPC fits telemetry

- supports unary RPCs and streaming RPCs,
- strongly typed service/message definitions,
- efficient binary serialization with Protobuf,
- long-lived bidirectional connections are possible,
- code generation in multiple languages.

## gNMI relationship

Do not say "gRPC and gNMI are the same".

```text
gNMI = network-management service semantics
   ↓ implemented using
gRPC = RPC framework
   ↓ uses
HTTP/2 over TCP
```

## Failure implications

A stream can be interrupted by:
- TCP failure,
- TLS/authentication problem,
- device restart,
- collector restart,
- keepalive/session timeout,
- path/model error.

The collector must reconnect and the NDT must be able to identify stale state during the gap.
