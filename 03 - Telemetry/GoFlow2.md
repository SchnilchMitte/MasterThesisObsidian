---
title: "GoFlow2"
tags: [goflow2, sflow, kafka]
---
# GoFlow2

GoFlow2 is a flow collector/normalizer supporting protocols including sFlow, NetFlow and IPFIX.

## Project path

```text
QFX
 ↓ sFlow
GoFlow2
 ↓ normalize
common flow representation
 ↓ Protobuf
Kafka
```

## Why a normalizer is useful

Different flow-export protocols have different record formats. A normalizer lets downstream consumers operate on one representation instead of implementing every exporter format.

The GoFlow2 documentation maps sFlow/NetFlow/IPFIX fields into a common Protobuf-oriented representation with fields such as receive time, sequence number, sampling rate and sampler address.

## Thesis relevance

GoFlow2 is an example of a **collector boundary**:
- protocol-specific input on the physical-network side,
- normalized event on the Kafka side.

Questions to document:
- where it runs,
- exact sFlow listen port,
- exact Protobuf schema/version,
- Kafka key/topic configuration,
- timestamp handling,
- batching and failure behavior.

## Source

- GoFlow2 protocols: https://github.com/netsampler/goflow2/blob/main/docs/protocols.md
- GoFlow2 repository: https://github.com/netsampler/goflow2
