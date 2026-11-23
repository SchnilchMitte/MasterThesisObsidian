---
title: "Project Data Domains"
tags: [project, data]
---
# Project Data Domains

## Device telemetry

Source: QFX/Junos via [[03 - Telemetry/gNMI]].

Examples:
- CPU / memory / temperature
- interface operational state
- octet/packet counters
- drops/errors/discards
- queue/QoS metrics where exposed
- hardware/component state

## Flow telemetry

Source: QFX via [[03 - Telemetry/sFlow]], collected by [[03 - Telemetry/GoFlow2]].

Examples:
- sampled source/destination information
- protocol and ports if present in sampled header
- ingress/egress interface metadata
- packet/byte-related information
- sampling rate and exporter identity

## Topology and control state

Source: [[06 - SDN/Ryu]] and/or another topology service.

Examples:
- nodes
- links
- link properties
- forwarding state
- installed flow rules
- path/control intent

## Experiment metadata

Source: [[08 - Experimentation/ExperimentRunner]].

Examples:
- experiment ID
- start/end time
- traffic profile
- topology/configuration version
- failure injection
- software/config version

## NDT-derived data

Examples:
- predictions
- optimization recommendations
- state-quality/confidence indicators
- anomaly scores
- control intents

The key thesis question is not just transporting these data, but maintaining a trustworthy relationship between **event time in the physical network** and **state applied inside the NDT**.
