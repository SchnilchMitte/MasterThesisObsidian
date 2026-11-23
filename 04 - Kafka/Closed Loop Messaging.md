---
title: "Closed Loop Messaging"
tags: [kafka, closed-loop, sdn]
---
# Closed Loop Messaging

## Recommended flow

```mermaid
flowchart LR
    NDT -->|intent| I[net.control.intent.v1]
    I --> V[Validator / Policy Service]
    V -->|validated command| C[net.control.command.v1]
    C --> A[Ryu Adapter]
    A --> R[Ryu]
    R --> Q[QFX]
    A -->|result| RES[net.control.result.v1]
    RES --> NDT
    Q -->|observed telemetry| T[Telemetry Topics]
    T --> NDT
```

## Intent vs command

**Intent** expresses desired outcome at higher level.

Example: "Move traffic demand X away from congested path."

**Command** is validated and concrete enough for a control adapter.

Example: "Install/update this specific forwarding rule on target SW04."

## Correlation

Every intent/command should carry:
- `intent_id`,
- `command_id`,
- target,
- creation time,
- expiry/deadline,
- desired state/version,
- experiment/run ID where relevant.

Results reference `command_id`.

## Status model

Useful statuses:
- `RECEIVED`
- `VALIDATED`
- `REJECTED`
- `SENT_TO_CONTROLLER`
- `ACCEPTED`
- `FAILED`
- `OBSERVED_EFFECT` (derived after telemetry confirms result)

## Safety principle

The NDT should not directly push arbitrary raw actions into the physical network without validation, authorization, idempotency checks, expiry handling, and observability.
