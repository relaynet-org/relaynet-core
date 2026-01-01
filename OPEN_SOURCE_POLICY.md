# Open Source Policy

This document defines the open-source scope and boundaries of the RelayNet project.

## Open Core Principle

RelayNet follows an **open-core model**.

This repository (`relaynet-core`) contains the **core relay rules and protocol engine**
and is licensed under **GNU AGPL v3**.

The goal of open-sourcing the core is to ensure:

- Transparency of relay rules and state transitions
- Auditability of cross-organization responsibility handoff
- Trust neutrality across participating organizations

## What Is Included in This Repository

The following components are considered part of the open core:

- Relay task and stage data models
- Relay state machine definitions
- Event and audit models
- Core workflow logic and protocol APIs

## What Is NOT Included

The following components are intentionally excluded from this repository
and may be provided under separate commercial licenses:

- User interfaces (UI / dashboards)
- Industry-specific templates or configurations
- Deployment tooling and operational scripts
- Monitoring, SLA, or compliance extensions
- Enterprise-only features

## Licensing Summary

- Open core (`relaynet-core`): GNU AGPL v3
- SDKs and client libraries: Permissive licenses (e.g. Apache 2.0)
- Commercial distributions: Separate commercial license

This separation is intentional and fundamental to the RelayNet project.
