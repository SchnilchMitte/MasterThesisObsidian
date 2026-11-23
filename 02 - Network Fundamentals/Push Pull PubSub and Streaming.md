---
title: "Push Pull PubSub and Streaming"
tags: [architecture, messaging, streaming]
---
# Push, Pull, Publish/Subscribe and Streaming

## Push

Producer actively sends data to receiver. Example: an sFlow exporter sends datagrams to a collector.

## Pull

Consumer requests data from source. Prometheus normally pulls/scrapes metrics from HTTP endpoints.

## Subscription / streaming

gNMI `Subscribe` is initiated by the client, then the device streams updates over the established RPC. It is therefore not simply "polling" even though the client initiates the subscription.

## Publish/subscribe

A producer publishes to an intermediary. Consumers subscribe independently. Kafka provides topic-based event distribution, while retaining events according to configured retention.

## Why terminology matters

- **event-driven architecture**: components react to events.
- **message-oriented middleware**: middleware exchanging discrete messages.
- **event streaming**: continuous, ordered streams of events with stream/log semantics.
- **streaming telemetry**: network state is continuously delivered rather than periodically fetched with individual polling requests.

In the thesis, use terminology consistently and avoid treating these as synonyms.
