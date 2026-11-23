---
title: "TCP-IP Stack"
tags: [networking, tcp, udp, ip]
---
# TCP/IP Stack

A practical Internet stack can be viewed as:

1. Application
2. Transport
3. Internet
4. Link

## TCP

Connection-oriented reliable byte stream. Important properties:
- sequence numbers and retransmission
- ordered delivery to the application
- congestion control
- flow control
- connection state

Used underneath gRPC/HTTP2, Kafka, HTTP/Prometheus.

## UDP

Connectionless datagrams. No built-in retransmission, ordered delivery, or connection state.

Used commonly for sFlow export because telemetry can prioritize low overhead over per-datagram delivery guarantees.

## IP

Provides addressing and routing between hosts. IP itself does not guarantee delivery or order.

## Ethernet

Frames are switched based primarily on MAC addresses inside a Layer-2 domain. VLANs can logically segment Layer-2 networks.

## Practical implication

Reliability is layered. For example, Kafka uses TCP for reliable transport, but Kafka's own acknowledgement/replication semantics decide when an event is considered durably accepted. Conversely, UDP-based sFlow can lose datagrams without application-level recovery.
