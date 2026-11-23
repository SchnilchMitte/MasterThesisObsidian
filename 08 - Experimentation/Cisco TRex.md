---
title: "Cisco TRex"
tags: [trex, experimentation, traffic]
---
# Cisco TRex

TRex is an open-source traffic generator powered by DPDK. It supports stateful and stateless traffic generation and can produce L3-L7 traffic.

## Project role

TRex is the **stimulus/load generator**, not a telemetry system.

```text
TRex → QFX network → resulting load/state → telemetry observes effects
```

## What it enables

Controlled scenarios such as:
- fixed offered load,
- ramping load,
- different flow counts,
- different packet sizes,
- sustained congestion,
- repeatable traffic profiles.

## Thesis use

TRex lets the experiment know what load was intentionally introduced, which makes telemetry and NDT response measurable under controlled conditions.

## Source

- TRex: https://trex-tgn.cisco.com/
