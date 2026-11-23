---
title: "Kafka Schema Evolution and Registry"
tags: [kafka, schema, protobuf]
---
# Schema Evolution and Registry

## Why schemas evolve

Telemetry events will change as new fields, timestamps, topology data and control metadata are added.

## Protobuf evolution

Safe evolution generally means adding new optional-compatible fields with new field numbers and never reusing an existing field number for unrelated semantics.

## Schema registry concept

A schema registry is a separate service/pattern that stores schema versions and can enforce compatibility rules. Kafka itself transports bytes and does not inherently provide domain-schema governance.

## Thesis recommendation

At minimum define:
- schema owner,
- version field / topic-version policy,
- compatibility rules,
- behavior for unknown fields/versions,
- dead-letter handling.

A registry may be useful but is not mandatory for the first prototype. Avoid adding infrastructure unless it solves a demonstrated requirement.
