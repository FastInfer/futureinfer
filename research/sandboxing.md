# Sandboxing & Runtime Isolation

The execution-isolation layer below the framework. Five players have emerged as the de facto sandbox layer for agents in production.

## Major platforms (2026)

| Platform | Isolation | Notes |
|---|---|---|
| E2B | Firecracker microVMs | 150ms cold starts |
| Modal | gVisor | Serverless pricing |
| Daytona | — | Open-source |
| Northflank | gVisor | BYOC deployment model |
| Sprites.dev | — | — |

The fact that this layer has 5 commercial players signals the framework layer (LangChain et al.) couldn't satisfy production needs alone. Tool execution had to be commoditised separately.

## Capability sandboxing & MCP gateway

Tool misuse is increasingly addressed via capability sandboxing and MCP security gateways rather than at the model layer. The pattern: the model can ask, but the gateway decides what is actually allowed.

## What's still missing

- **Cross-platform portability** — no standard for moving an agent execution between sandboxes.
- **Declarative resource budgets** — no standard for "this agent may use X CPU, Y network, Z dollars."
- **Audit-trail standardisation** — every platform has its own log format.
- **Local sandboxing on user-owned hardware** — the OpenClaw model. Host is trusted, tools are not. Clean threat model that the cloud sandboxes do not address.

## Threads to go deeper

- [ ] E2B vs Modal: detailed comparison of isolation guarantees, threat models, exit-vector coverage.
- [ ] Daytona — read the source. What is the isolation primitive? How does it compare to Firecracker / gVisor?
- [ ] Is there a sandbox-agnostic agent runtime spec? If not, why not? Who would write one?
- [ ] How does OpenClaw handle sandboxing on a user's own machine? What stops a tool from escalating to the host?
- [ ] What does the [Microsoft Agent Governance Toolkit](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/) actually provide at the runtime level? Does it overlap with what E2B/Modal sell?
- [ ] Performance vs isolation: at what cold-start budget do agents become uncomfortable to use? E2B claims 150ms — what is the real perceived ceiling?

## Sources

- [The Sandboxing Problem No One Has Solved — SoftwareSeni](https://www.softwareseni.com/ai-agents-in-production-the-sandboxing-problem-no-one-has-solved/)
- [Security for Production AI Agents in 2026 — Iain Harper](https://iain.so/security-for-production-ai-agents-in-2026)
- [Microsoft Agent Governance Toolkit](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/)
