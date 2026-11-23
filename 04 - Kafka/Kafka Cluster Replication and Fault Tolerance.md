---
title: "Kafka Cluster Replication and Fault Tolerance"
tags: [kafka, replication, reliability]
---
# Kafka Cluster, Replication and Fault Tolerance

## Broker cluster

A Kafka cluster consists of broker processes storing topic partitions and serving producers/consumers.

## Replication

A partition can have multiple replicas. One replica is the leader for client reads/writes and other replicas follow it. Replication allows service to continue after certain broker failures depending on configuration and replica state.

## Why this matters

"Kafka accepted the event" can have different durability meaning depending on:
- replication factor,
- number of in-sync replicas,
- producer `acks`,
- broker/topic durability settings.

## Thesis principle

Do not evaluate only latency. Document the durability setting associated with each latency result. A configuration that is 1 ms faster but loses records on a broker failure is not directly comparable to a stronger-durability configuration.

## Source

- Apache Kafka documentation/design: https://kafka.apache.org/documentation/
