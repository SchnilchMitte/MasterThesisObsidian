---
title: "OSI Model"
tags: [networking, osi, fundamentals]
---
# OSI Model

The OSI model is a conceptual reference model. Real Internet stacks do not map perfectly one-to-one, but the model helps locate responsibilities.

| Layer | Name | Typical examples in this project | Core question |
|---:|---|---|---|
| 7 | Application | gNMI, HTTP API, Prometheus exposition, Kafka client protocol conceptually | What application semantics are exchanged? |
| 6 | Presentation | Protobuf, JSON, text exposition, TLS representation/encryption functions | How are data represented/encoded? |
| 5 | Session | long-lived gRPC sessions, application sessions | How is an application conversation maintained? |
| 4 | Transport | TCP, UDP | reliable byte stream or datagrams? |
| 3 | Network | IPv4/IPv6 | how are packets routed between IP endpoints? |
| 2 | Data Link | Ethernet, VLAN, MAC | local frame delivery / switching |
| 1 | Physical | 10GbE, 100GbE, fiber/copper | bits/signals on medium |

## Project stack examples

### gNMI telemetry

```text
gNMI                 Application
Protobuf             Representation
 gRPC
 HTTP/2              Application/session-ish transport framework
 TCP                  Transport
 IP                   Network
 Ethernet             Data link
 10/100GbE medium     Physical
```

### sFlow

```text
sFlow                 Application telemetry protocol
UDP                   Transport
IP                    Network
Ethernet              Data link
Physical medium       Physical
```

### Kafka

```text
Kafka client protocol Application
TCP                   Transport
IP                    Network
Ethernet              Data link
Physical medium       Physical
```

## Thesis relevance

When measuring latency, distinguish application processing from transport/network delay. "Kafka latency" may actually contain collector processing, serialization, queueing, network transport, broker append, consumer fetch, deserialization, and NDT apply time.
