---
title: "Thesis Working Structure"
tags: [thesis, outline]
---
# Thesis Working Structure

## 1 Introduction
- Motivation
- Problem statement
- Research questions
- Contributions

## 2 Background
- Network Digital Twins
- Networking/planes
- Streaming telemetry
- Flow telemetry
- Event streaming/messaging
- SDN and closed-loop control

## 3 Related Work
- NDT architectures
- NDT synchronization
- telemetry/message-broker architectures
- event-streaming in networking

## 4 Existing Testbed
- physical topology
- management vs data network
- TRex and ExperimentRunner
- gNMI/Telegraf/Prometheus pipeline
- sFlow/GoFlow2/Kafka pipeline
- Ryu/control infrastructure

## 5 Requirements and Architecture
- NDT synchronization requirements
- technology selection criteria
- Kafka hub architecture
- topic/schema/key design
- current-state vs event-history model
- closed-loop design

## 6 Implementation
- gNMI → Telegraf → Kafka
- sFlow → GoFlow2 → Kafka
- topology/control-state integration
- NDT consumer/state builder
- monitoring integration
- NDT → Kafka → Ryu path

## 7 Experimental Methodology
- metrics
- load scenarios
- failure scenarios
- deployment/scaling scenarios
- reproducibility

## 8 Evaluation
- latency/freshness
- reliability/recovery
- scalability/throughput
- network overhead/resource cost
- closed-loop behavior

## 9 NDT Health / Observability
- health model
- fault differentiation
- dashboards/metrics

## 10 Discussion
- interpretation
- testbed limitations
- real-deployment implications
- threats to validity

## 11 Conclusion
