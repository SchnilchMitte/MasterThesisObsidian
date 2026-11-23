---
title: "IP Address Plan"
tags: [project, networking, ip]
---
# IP Address Plan

## Management plane

Network: `172.20.202.*`

| Host                     | IP               |
| ------------------------ | ---------------- |
| NUC1 / Orchestrator      | `172.20.202.41`  |
| NUC2 / Traffic Generator | `172.20.202.42`  |
| NUC3 / Traffic Generator | `172.20.202.43`  |
| NUC4 / Traffic Generator | `172.20.202.44`  |
| NUC5 / Traffic Generator | `172.20.202.45`  |
| SW01                     | `172.20.202.151` |
| SW02                     | `172.20.202.152` |
| SW03                     | `172.20.202.153` |
| SW04                     | `172.20.202.154` |
| SW05                     | `172.20.202.155` |
| SW06                     | `172.20.202.156` |
| SW07                     | `172.20.202.157` |
| SW08                     | `172.20.202.158` |

## Data plane

Network: `172.20.2.*`

Exact endpoint/interface assignments are **TBD**.

## Why the distinction matters

The thesis should explicitly record for every connection whether it uses management or data networking. A low-latency NDT pipeline over a dedicated management network is not equivalent to the same pipeline sharing production links.
