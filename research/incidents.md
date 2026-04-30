# Production Incidents

Concrete failures with primary references. These are existence proofs that specific gaps are real, not speculative.

## CVE-2025-53773 — RCE via prompt injection in GitHub Copilot

Researchers achieved remote code execution against GitHub Copilot by embedding malicious instructions in repository files the agent analysed.

Mechanism: indirect prompt injection — untrusted text in a file is read by the agent and interpreted as instructions, escalating into code execution.

Implication: code-reading agents need provenance / trust boundaries on **inputs**, not just on outputs. The model layer cannot reliably distinguish data from instructions.

## Asana — tenant isolation flaw

AI agent surface affected up to **1,000 enterprises** through a multi-tenant isolation flaw.

Implication: multi-tenant agent isolation is unsolved at the product layer, not just at the runtime layer. Every B2B SaaS adding an agent surface is exposed to this class.

## WordPress plugins — privilege escalation

100,000+ sites exposed via AI plugin vulnerabilities (multiple CVEs in 2025).

Implication: the long tail of agent integrations (plugins, extensions) has a much weaker security posture than the flagship products.

## Galileo — cascading failure in multi-agent systems

A single compromised agent poisons **87% of downstream decisions within 4 hours** in MAS networks. Faster than traditional incident response can contain.

Implication: blast-radius containment in MAS isn't theoretical. Speed of propagation is the new variable that classical SRE playbooks don't handle.

## Threads to go deeper

- [ ] CVE-2025-53773 — read the disclosure for the exact injection vector and proposed mitigations. Was the fix at model, runtime, or product layer?
- [ ] Asana incident report — was the flaw in their agent runtime, the framework, or the integration glue?
- [ ] Catalogue all 2025–2026 agent-related CVEs from MITRE — frequency, root-cause distribution, layer where the fix lives.
- [ ] Galileo MAS finding — read the underlying methodology. Is the "87% in 4 hours" reproducible, or marketing?
- [ ] Are there any documented incidents involving local-first agents (e.g. OpenClaw) yet? If not, why — too new, or genuinely safer architecture?
- [ ] Look for postmortems in the [LLMOps Database (ZenML)](https://www.zenml.io/llmops-database) — concrete production failure narratives.

## Sources

- [eSecurity Planet — AI Agent Attacks Q4 2025](https://www.esecurityplanet.com/artificial-intelligence/ai-agent-attacks-in-q4-2025-signal-new-risks-for-2026/)
- [Adversa AI — Top Agentic AI Security Resources Dec 2025](https://adversa.ai/blog/top-agentic-ai-security-resources-december-2025/)
- [Stellar Cyber — Top Agentic AI Threats 2026](https://stellarcyber.ai/learn/agentic-ai-securiry-threats/)
- [Rippling — Agentic AI Security 2025](https://www.rippling.com/blog/agentic-ai-security)
