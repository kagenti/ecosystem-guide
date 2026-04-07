# Observability & Token Management

**Core Contributors:** Evaline Ju, Ilya Kolchinsky

**Resources:** [Box notes](https://ibm.ent.box.com/notes/2070946778010?s=0c0s3lt3o4avpxpgwxdgas3axaq225bg)

## Description

Observability and token management for the agentic platform.

## Active Work

**Smart auto-instrumentation operator (PoC)** — Ilya Kolchinsky has built a Kubernetes operator for advanced OpenTelemetry auto-instrumentation of AI agent deployments. Features: per-library control without custom images, automatic detection of existing instrumentation, pluggable architecture. Written to be mergeable into kagenti-operator / AgentRuntime CR. Repo: https://github.com/ilya-kolchinsky/agent-observability-operator
