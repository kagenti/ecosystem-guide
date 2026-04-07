# Agent Runtime

**Core Contributors:** Mariusz Sabath, Paolo Dettori

## Description

The layer responsible for handling what happens when an agent is actively executing on the platform. Guardrails, evals, routing, context flowing in and out of the LLM in the moment.

- **Core runtime** covers the bridge between agent lifecycle and the broader platform, handling tasks that extend beyond basic auth into things like network-level agent management.
- **Context-based guardrails & evals** - Haifa's team is being embedded into this workstream specifically to handle guardrails and evals that operate at the context level, meaning they're inspecting/constraining what flows in and out of the LLM during agent execution.
