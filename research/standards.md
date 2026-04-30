# Standards & Governance

Emerging security and governance frameworks for agentic systems. The fact that these exist *now* — not in 2023 — is itself the signal that the layer is immature.

## OWASP Agentic AI Top 10 (December 2025)

First formal taxonomy of agent-specific risks. Categories:

1. Goal hijacking
2. Tool misuse
3. Identity abuse
4. Supply chain risks
5. Code execution
6. Memory poisoning
7. Insecure communications
8. Cascading failures
9. Human-agent trust exploitation
10. Rogue agents

Each category maps to one or more research questions in FutureInfer's README. This is the most useful single artifact for grounding the README's "open questions" section.

## Model Context Protocol (MCP) Security

**Source:** [Coalition for Secure AI — Securing the AI Agent Revolution: A Practical Guide to MCP Security](https://www.coalitionforsecureai.org/securing-the-ai-agent-revolution-a-practical-guide-to-mcp-security/)

Practical guide to MCP-specific security concerns:

- Tool description trust — the model trusts whatever a tool says it does.
- Capability scoping — what the tool may read/write/reach.
- Server identity verification.

MCP became the de facto tool protocol; its security model is therefore load-bearing.

## Microsoft Agent Governance Toolkit

**Source:** [opensource.microsoft.com — April 2026](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/)

Open-source runtime security primitives. Released April 2026. Notable because: this is being open-sourced *now*, not in 2024 — runtime security wasn't solved (and is being commoditised mid-2026).

## 2025 AI Agent Index (MIT)

**Source:** [aiagentindex.mit.edu](https://aiagentindex.mit.edu/data/2025-AI-Agent-Index.pdf) — also as [arxiv preprint](https://arxiv.org/html/2602.17753v1)

Documents technical and safety features of deployed agentic systems. Useful as a snapshot of what's actually shipped vs what's claimed in marketing.

## Threads to go deeper

- [ ] Map OWASP Top 10 → existing framework coverage. Which frameworks address which categories, and how?
- [ ] MCP security: what does and doesn't compose under current implementations? Where are the trust boundaries?
- [ ] MIT AI Agent Index — extract claims-vs-reality data on memory and verification specifically.
- [ ] Cross-reference OWASP categories with the documented CVEs in [incidents.md](incidents.md). Are the categories well-calibrated, or are real attacks landing in a 2nd-order category not on the list?
- [ ] Is there an emerging spec for **audit trails** of agent actions? If not, that is a clean substrate gap.
- [ ] EU AI Act implications for agentic systems — what compliance work is in flight, and what does it imply for verification/audit primitives?

## Sources

- [OWASP Agentic AI Top 10 (via Adversa AI)](https://adversa.ai/blog/top-agentic-ai-security-resources-december-2025/)
- [Coalition for Secure AI — MCP Security](https://www.coalitionforsecureai.org/securing-the-ai-agent-revolution-a-practical-guide-to-mcp-security/)
- [Microsoft Agent Governance Toolkit](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/)
- [MIT 2025 AI Agent Index](https://aiagentindex.mit.edu/data/2025-AI-Agent-Index.pdf)
