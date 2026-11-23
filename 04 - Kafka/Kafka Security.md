---
title: "Kafka Security"
tags: [kafka, security, closed-loop]
---
# Kafka Security

A production-quality central hub must consider confidentiality, authentication, authorization and integrity.

## Main areas

- TLS for encrypted broker/client transport,
- client authentication such as SASL mechanisms or certificates,
- ACLs/authorization for topic access,
- credential/certificate management,
- separation of telemetry-read permissions from control-write permissions.

## Closed-loop requirement

Control topics are higher risk than read-only telemetry topics. The NDT should not automatically receive permission to perform every network operation.

Suggested security boundary:

```text
NDT writes intent
  ↓
validation/policy service
  ↓ restricted identity
control command
  ↓
Ryu adapter
```

Security may be outside experimental scope, but the architecture discussion should acknowledge it.
