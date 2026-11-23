---
title: "Kafka Delivery Ordering and Reliability"
tags: [kafka, reliability, ordering]
---
# Delivery, Ordering and Reliability

## Ordering

Kafka ordering is per partition. Correct key design is therefore a state-consistency mechanism, not just a performance setting.

## Producer acknowledgements

Producer reliability depends on settings such as acknowledgements, retries, idempotence, replication, and broker/topic durability settings.

Conceptually:
- low acknowledgement requirement can reduce waiting but weakens durability,
- stronger acknowledgement waits for more durable replication state,
- idempotent production helps prevent duplicate records caused by producer retries.

## Consumer processing semantics

A consumer must decide when to commit progress relative to processing:

```text
fetch → process → apply NDT state → commit
```

versus

```text
fetch → commit → process
```

The ordering changes whether a crash risks duplicate processing or lost processing.

## Control-loop rule

Control operations should be designed to be **idempotent** where possible. A duplicate delivery of `SET_ROUTE desired_state=X` is safer than a non-idempotent instruction like `increment metric` or `toggle state`.

## Physical confirmation

A Kafka `control.result=APPLIED` does not prove the physical network has converged. The strongest closed-loop confirmation is new telemetry observing the intended physical state.
