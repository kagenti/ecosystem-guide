# About Kagenti

Kagenti is an open source ecosystem for building, deploying, securing, and governing AI agents on Kubernetes. It spans the full agent lifecycle — from local development and testing, through production deployment, to runtime security and observability.

It's framework-neutral: agents built with LangGraph, CrewAI, AG2, AutoGen, or any A2A-compatible framework all run on Kagenti. Communication uses open standards — A2A (Agent-to-Agent protocol) and MCP (Model Context Protocol) — so teams aren't locked into any vendor's stack.

The project started in early 2025 out of IBM Research with deep collaboration from Red Hat, and has grown to 12 repos, 43 org members, and 80+ contributors across both organizations.

## The Problem

Every major tech company is building AI agents. Frameworks and harnesses for creating them are maturing fast. But there is no mature, widely adopted ecosystem designed to take agents from development to production. No standard way to build them, deploy them, secure their identities, govern what they can access, or observe what they're doing at scale.

This is the same gap Kubernetes filled for containers a decade ago. Agents are the new workload, and they need their own ecosystem — before enterprises start deploying them without one.

## What the Ecosystem Covers

| Area | What it does |
|------|-------------|
| **Developer Tooling** | ADK — CLI, Python + TypeScript SDKs, and a local dev environment. Build and test agents without a cluster. |
| **Lifecycle Orchestration** | Deploy agents and tools as containers via AgentCard CRDs. Auto-build with Shipwright. Discovery and registration handled by the operator. |
| **Networking** | MCP Gateway routes tool calls across agents. Istio service mesh for mTLS. Gateway API for ingress. |
| **Security** | Zero-trust from the ground up. SPIFFE/SPIRE for cryptographic workload identity. Keycloak for OAuth/OIDC. AuthBridge for token exchange. No static credentials. |
| **Observability** | Distributed tracing via MLflow, Langflow, and Phoenix. Network visualization through Kiali. Token cost attribution. OpenTelemetry auto-instrumentation. |
| **Security Testing** | Capture the Flag — red-team scenarios with real AI agents probing for policy violations. |
| **Benchmarking** | Agent benchmarking and test infrastructure for evaluating agent behavior at scale. |

## Community

The community ships weekly, publishes on [Medium](https://medium.com/kagenti-the-agentic-platform), and has presented at KubeCon NA 2025, KubeCon EU 2026, and The Cloudcast podcast.

See [Blogs](blogs.md) for the full list of blogs, demos, and coverage.
