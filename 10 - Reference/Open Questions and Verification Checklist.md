---
title: "Open Questions and Verification Checklist"
tags: [todo, project, verification]
---
# Open Questions and Verification Checklist

## Hosts/services

- [ ] Which physical switch in the diagram maps to SW01…SW08?
- [ ] Exact `172.20.2.*` data-plane addresses/interfaces?
- [ ] Where does GoFlow2 run?
- [ ] Where does Kafka run and how many brokers exist?
- [ ] Where does Ryu run?
- [ ] Where does Grafana run?
- [ ] Where does ExperimentRunner run?

## gNMI / Telegraf

- [ ] Exact gNMI port: `50051`, `5051`, or another value?
- [ ] TLS enabled? certificates/authentication?
- [ ] Exact gNMI subscription paths/origins?
- [ ] Subscription mode and intervals?
- [ ] Which timestamps are emitted and preserved?
- [ ] Telegraf Prometheus endpoint port: `9126` or other?
- [ ] Existing Telegraf processors/filters?

## sFlow / GoFlow2

- [ ] Exact sFlow destination IP/UDP port?
- [ ] Sampling rate per switch/interface?
- [ ] GoFlow2 Protobuf schema/version?
- [ ] Kafka topic/key currently used?
- [ ] Meaning of "Kafka → Manuel" in the team note?

## Kafka

- [ ] Kafka version?
- [ ] brokers/controllers/storage layout?
- [ ] replication factor?
- [ ] authentication/TLS?
- [ ] existing topics and partition counts?
- [ ] current retention/compression settings?
- [ ] current consumers?

## Ryu / SDN

- [ ] Exact Ryu application?
- [ ] Southbound protocol: OpenFlow, NETCONF, other?
- [ ] How topology is discovered?
- [ ] How forwarding changes are applied?
- [ ] How errors/acks are exposed?

## Time synchronization

- [ ] NTP or PTP?
- [ ] clock offset among QFX, NUCs, Kafka, NDT?
- [ ] precision required for latency measurements?

## Thesis architecture

- [ ] canonical Kafka event schema?
- [ ] topic/key/partition strategy?
- [ ] event retention vs compacted state topics?
- [ ] NDT bootstrap strategy?
- [ ] control intent validation policy?
- [ ] physical-state confirmation strategy?
