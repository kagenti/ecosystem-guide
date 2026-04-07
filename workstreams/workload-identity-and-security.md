# Workload Identity and Security

**Core Contributors:** Mariusz Sabath, Maia Iyer, Alan Cha, Morgan Foster, Akram Ben Aissi

**Slack:** [kagenti-identity](https://ibm.enterprise.slack.com/archives/C0AFNRQSC22)

**Resources:** [Box folder](https://ibm.box.com/s/zhgg0nxtc7118qc315sf10au3cethm9t)

## Description

Authentication and identity management for agents and users. Zero-trust architecture with SPIFFE/SPIRE workload identity, Keycloak (OAuth/OIDC), AuthBridge for token exchange.

## Active Work

**Istio Waypoint auth simplification** — Akram Ben Aissi has been testing an Istio/waypoint solution to replace the 2-sidecar approach (spiffe-helper + envoyproxy) for agent token validation and token exchange. Successfully tested on kagenti OpenShift. Trades sidecar complexity for waypoint config complexity. Under evaluation vs. other solutions given Istio's modest market share in OpenShift/RHOAI installations. [Design doc (Google Docs)](https://docs.google.com/document/d/...)

**SPIFFE/SPIRE Stacking Multiple Workload Attestors** — Mariusz Sabath is drafting a proposal for the SPIRE community on stacking multiple workload attestors, relevant to AgentCard signing. Morgan Foster collaborating.

**Capture the Flag (security benchmarking)** — Morgan Foster created CTF scenarios to red-team Kagenti security. Tests real-world policy enforcement (e.g., preventing Claude Code from exfiltrating PII via leaked access tokens). Repo: [kagenti/capture-the-flag](https://github.com/kagenti/capture-the-flag)

**Webhook migration to operator** — Varsha Prasad Narsing is porting the sidecar injection webhook (~7K lines) from kagenti-extensions/kagenti-webhook into kagenti-operator. Branch: `feat/webhook-migration`. Benefits: typed CRD access, single-binary deployment, CR-driven injection via AgentRuntime CR.
