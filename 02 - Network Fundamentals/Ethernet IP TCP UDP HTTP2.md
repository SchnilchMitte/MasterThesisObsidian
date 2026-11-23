---
title: "Ethernet IP TCP UDP and HTTP2"
tags: [networking, fundamentals]
---
# Ethernet, IP, TCP, UDP and HTTP/2

## Ethernet

Layer-2 framing and switching. A frame carries source/destination MAC addresses and a payload such as an IP packet. The project diagram shows 10 GbE and 100 GbE physical/data-link connectivity.

## IP

Layer-3 packet addressing. Management and data networks use separate IPv4 ranges in the project.

## TCP

Reliable, ordered stream. Used by:
- gRPC/HTTP2 for gNMI
- HTTP for Prometheus/Grafana/API traffic
- Kafka client-broker communication

## UDP

Datagram transport. Used commonly by sFlow exporters toward collectors.

## HTTP/2

Multiplexed HTTP version used by gRPC. Multiple logical streams can share a TCP connection. gRPC uses HTTP/2 framing but presents RPC semantics to applications.

## Why this matters for telemetry

A telemetry stream can experience:
- serialization delay,
- socket buffering,
- TCP retransmission,
- congestion control delay,
- switch queueing,
- collector processing,
- broker queueing,
- consumer polling delay.

End-to-end freshness is the sum of these effects, not a property of one protocol alone.
