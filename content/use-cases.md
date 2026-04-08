# Use Cases & Personas

> **Note:** This page is a WIP.

Kagenti serves two primary personas. Everything the platform does flows from their needs. A third persona, the Platform Operator, enables the governance and trust guarantees that both primary personas depend on.

---

## Personas

### Agent Developer

Builds AI agents using any framework (LangGraph, CrewAI, AG2, or any A2A-compatible framework) and deploys them to Kubernetes via Kagenti. Wants to focus on agent logic, not infrastructure plumbing.

**Core needs:**

- Deploy agents with one command, iterate fast
- Access internal and external services without managing credentials or network rules
- Compose multi-agent workflows with secure agent-to-agent communication
- Get observability (traces, token usage, tool calls) without writing instrumentation code
- Control who can access my agent while I iterate

### End User

Business users and developers who interact with deployed agents through the Kagenti UI or APIs. Doesn't care how agents are built or where they run.

**Core needs:**

- Find and use agents relevant to my work
- Submit tasks (including long-running ones) and get results back
- Trust that agents are safe, authorized, and operating within policy
- Access only the agents and data I'm permitted to see

### Platform Operator *(enterprise context)*

Administers the Kagenti platform: deploys infrastructure, sets policies, manages multi-tenancy. The reason Agent Developers can "just deploy" and End Users can trust what they're interacting with.

**Core needs:**

- Control which AI models and external services each team can use
- Enforce content safety and compliance policies uniformly across all agents
- Isolate teams with per-namespace telemetry, quotas, and access boundaries
- Verify agent provenance and block unverified deployments
- See everything running across the platform and respond when things go wrong

---

## Use Case Types

Kagenti supports five operational models. Each has distinct security, lifecycle, and infrastructure requirements.

| Type | Description | Example |
|------|-------------|---------|
| **Knowledge & Analysis** | Read-only retrieval and synthesis of organizational content. No external actions. | Compliance assistant that summarizes policy sections with citations. |
| **Synchronous Task** | Real-time, session-bound actions on the user's behalf using their permissions. | Creating a pull request in GitHub during an active chat session. |
| **Asynchronous Task** | Long-running, stateful workflows that continue after the user session ends. | Analyzing all 2025 pull requests and notifying the user when complete. |
| **Continuous Monitoring** | Persistent systems observing data streams and triggering automated responses. | Document classifier that watches a datastore and auto-tags new uploads. |
| **Event-Driven Automation** | Processes triggered by external events (webhooks, schedules, alerts). | GitHub webhook that triages new issues automatically. |

---

## User Stories

Outcome-focused stories organized by platform capability. Each describes *what the user needs*, not how to build it.

### Deployment & Access

**Deploy an agent that uses internal and external services**

As an **Agent Developer**, I want to deploy an agent that accesses both internal and external services, so that my agent can get its job done without me managing credentials or network rules for each service.

- Given my agent is deployed, when it calls an internal service, then it is automatically authenticated with only the permissions it needs
- Given my agent tries to reach an external service not on the approved list, then the request is denied and I see a clear error

**Keep my agent private while I iterate**

As an **Agent Developer**, I want to keep my deployed agent accessible only to me, so that I can experiment before anyone else sees it.

- Given I deploy an agent with private access, when a colleague tries to call it, then they receive an access denied error
- Given my agent is private, when I decide it's ready, then I can open access to my team without redeploying

**Share my agent with my team**

As an **Agent Developer**, I want to share my agent with specific teammates without filing a platform request, so that my team can start using it immediately.

- Given I own a deployed agent, when I add my team to its access list, then team members can call the agent within minutes

**Compose agents into workflows**

As an **Agent Developer**, I want my agents to call each other securely, so that I can build multi-agent workflows without opening access to agents I don't control.

- Given I own Agent A and Agent B, when I configure Agent A to call Agent B, then the call succeeds with proper authentication
- Given a third-party agent tries to call my Agent B without authorization, then the call is denied

### Observability

**Get traces without changing agent code**

As an **Agent Developer**, I want my agent to automatically produce traces, token usage metrics, and tool call logs, so that I can debug and optimize without adding instrumentation code.

- Given I deploy an agent with no instrumentation code, when the agent handles a request, then a trace is created showing the request flow, model calls, and tool invocations

### Developer Experience

**Deploy my local agent to the cluster in one step**

As an **Agent Developer**, I want to push my locally developed agent to a remote cluster with a single command, so that I can test against real infrastructure without a CI/CD pipeline.

- Given I have an agent running locally, when I run the deploy command, then my agent is built, pushed, and running in my namespace within minutes
- Given I'm done testing, then I can tear it down with a single command and leave no resources behind

**Test multi-agent interactions in a real environment**

As an **Agent Developer**, I want to test how my agents work together in a live cluster, so that I can validate inter-agent communication and data flow under realistic conditions.

- Given I deploy multiple agents in a test namespace, when Agent A calls Agent B, then authentication and authorization work the same as in production

### Async Work & Inbox

**Receive work from a queue without writing plumbing code**

As an **Agent Developer**, I want to declare where my agent's work comes from (a queue, a webhook, an event stream), so that the platform handles message delivery and I only write the business logic.

- Given I declare a queue as my agent's inbox, when a message arrives, then my agent receives it through the same interface as a direct call
- Given a message fails processing, when retries are exhausted, then it is moved to a dead-letter destination and I'm notified

**Submit a task and check back later**

As an **End User**, I want to submit a long-running task and get a handle to check on it later, so that I'm not stuck waiting for it to finish.

- Given I submit a task, when the agent accepts it, then I receive a task ID and a link to check the status
- Given my task is complete, when I check the status, then I see the result and can download any outputs

### Agent Discovery

**Find and use agents across the platform**

As an **End User**, I want to browse all agents available to me and filter by capability, so that I can find the right agent for my task.

- Given agents are deployed across multiple teams, when I open the agent catalog, then I see all agents I'm authorized to view with their status
- Given I need an agent with a specific skill, when I filter by capability, then only matching agents are shown

### Trust & Safety

**Know that agents are verified and safe**

As an **End User**, I want confidence that agents I interact with have been verified, built from trusted sources, and comply with content safety policies, so that I can use them without worrying about tampered or unsafe behavior.

- Given an agent is deployed, when I view it in the catalog, then I can see whether it has verified build provenance
- Given I submit a request, when it violates content safety policy, then it is blocked before reaching the agent
- Given an agent produces a response that violates policy, then the response is blocked and the violation is logged

---

## Platform Operator Stories

These stories describe the enterprise governance layer. They explain *how* the trust and safety guarantees above get enforced.

### Governance & Policy

**Control which AI models teams can use**

As a **Platform Operator**, I want to define which AI models and providers each team is allowed to use, so that I can manage costs and ensure only approved models are in production.

- Given I set an approved model list for a namespace, when an agent requests a non-approved model, then the request is rejected with a message naming the approved alternatives

**Control what external services agents can reach**

As a **Platform Operator**, I want to define which external endpoints each team's agents can access, so that I can prevent data exfiltration and enforce network boundaries.

- Given I define an allowlist for a namespace, when an agent tries to reach a domain not on the list, then the request is blocked and logged

**Enforce content safety across all agents**

As a **Platform Operator**, I want all agents to comply with the same content safety and compliance rules, so that no single agent can produce or accept content that violates our policies.

- Given I define a guardrails policy, when any agent receives a request that violates it, then the request is blocked before reaching the agent
- Given an agent developer deploys an agent, when they try to disable platform guardrails, then they cannot override the platform-level policy

### Identity & Trust

**Verify agent build provenance**

As a **Platform Operator**, I want deployed agents to carry proof of where they were built and from which source, so that I can verify an agent hasn't been tampered with before allowing it to run.

- Given an agent is built through our CI/CD pipeline, when it is deployed, then its build provenance is attached and verifiable
- Given I configure a policy requiring provenance, when an unverified agent is deployed, then it is blocked from running

### Observability & Multi-Tenancy

**Isolate team telemetry**

As a **Platform Operator**, I want each team's agent telemetry routed to their own dashboard, so that teams have full visibility into their agents without seeing other teams' data.

- Given I onboard a new team, when they deploy their first agent, then telemetry is automatically routed to their designated backend without the developer configuring anything

**Set spending limits per team**

As a **Platform Operator**, I want to set token usage budgets per team and optionally per agent, so that no team can run up unbounded inference costs.

- Given I set a daily token budget for a namespace, when an agent exceeds it, then further inference requests are rejected with a clear "budget exceeded" message

### Agent Lifecycle

**New agents start with limited access**

As a **Platform Operator**, I want new agents to start with restricted access and be promoted only after evaluation, so that untested agents cannot reach production resources or sensitive data.

- Given a new agent is deployed, when it starts running, then it has access only to a restricted set of services and endpoints
- Given I evaluate and approve a restricted agent, when I promote it, then it gains access to the full set of services defined for its namespace

### Fleet Visibility

**See all agents running across the platform**

As a **Platform Operator**, I want a unified view of all agents across all teams, so that I can understand what's running, where, and whether it's healthy.

- Given agents are deployed across multiple namespaces, when I open the agent catalog, then I see all agents I'm authorized to view with their status
- Given an agent becomes unhealthy, when I view the catalog, then its status reflects the problem in near real-time
