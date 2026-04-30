# Industry Reports

Primary accounts from labs running agents in production. Filter for what they actually struggled with, not what they pitched.

## Anthropic — Building Effective Agents

**Source:** [anthropic.com/research/building-effective-agents](https://www.anthropic.com/research/building-effective-agents)

Direct quotes worth holding onto:

- "The most successful implementations weren't using complex frameworks or specialized libraries — they were building with simple, composable patterns."
- "The last mile often becomes most of the journey."
- "The compound nature of errors in agentic systems means that minor issues for traditional software can derail agents entirely."

Recommends starting with LLM APIs directly. Many useful patterns are a few lines of code.

Implication: the framework layer (LangChain, AutoGen, CrewAI) is not where the value is. The value is in production-hardening — and nobody has packaged that.

## Anthropic — Multi-agent research system

**Source:** [anthropic.com/engineering/multi-agent-research-system](https://www.anthropic.com/engineering/multi-agent-research-system)

The "prototype-to-production" gap is named explicitly. Codebases that work on developer machines need significant engineering to become reliable production systems. Prompt engineering identified as the primary lever for behavior improvement — not architecture, not orchestration.

## Anthropic — Claude Agent SDK

**Source:** referenced in [Anthropic engineering blog index](https://www.engineering.fyi/company/anthropic) and [Building Production AI Agents — ZenML LLMOps Database](https://www.zenml.io/llmops-database/building-production-ai-agents-lessons-from-claude-code-and-enterprise-deployments)

Packages the agent loop, system prompts, tools, permission system, and memory management that power Claude Code into reusable primitives. Worth treating as a reference implementation of "what production primitives look like."

## Cognition — Devin 2025 Performance Review

**Source:** [cognition.ai/blog/devin-annual-performance-review-2025](https://cognition.ai/blog/devin-annual-performance-review-2025)

Concrete numbers, 14 months after launch:

- PR merge rate: **34% (2024) → 67% (2025)**
- 4× faster, 2× more resource-efficient
- ETL migrations: 3–4 hours per file vs 30–40 hours for humans (10×)

Honest framing: 1 in 3 agent PRs are still wrong. The arc from launch demo to production took 14 months and is incomplete.

## Cognition — Coding Agents 101

**Source:** [devin.ai/agents101](https://devin.ai/agents101)

Practitioner advice: engineers extracting most value do *not* delegate the hardest problems. They:

- Decompose work into agent-suitable chunks
- Review output as if from a junior developer
- Keep architecture decisions human

This is the inverse of the "autonomous agent" pitch and probably the most honest practitioner report in the space.

## Microsoft — Agent Governance Toolkit

**Source:** [opensource.microsoft.com — April 2, 2026](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/)

Open-source runtime security primitives for AI agents. Released April 2026. The signal: this is being open-sourced *now*, not in 2024 — runtime security wasn't solved.

## Threads to go deeper

- [ ] Anthropic "Writing Effective Tools for AI Agents" — extract specific tool-design failure patterns and what good tools look like.
- [ ] Devin's 33% failure: what category? (Cognition's 2025 review may have a breakdown — re-read carefully.)
- [ ] Microsoft Agent Governance Toolkit — read the actual primitives, compare coverage to OWASP Agentic Top 10.
- [ ] OpenAI Agents SDK design notes — why "lightweight" instead of "framework"?
- [ ] Claude Agent SDK — what is in the permission system specifically? Compare against MCP capability scoping.
- [ ] Find equivalent reports from: Replit Agent, Cursor, Sourcegraph Cody, Continue, Aider — does anyone disagree with Anthropic's "simple composable patterns" claim?

## Sources

- [Anthropic — Building Effective Agents](https://www.anthropic.com/research/building-effective-agents)
- [Anthropic — Multi-agent Research System](https://www.anthropic.com/engineering/multi-agent-research-system)
- [Cognition — Devin 2025 Performance Review](https://cognition.ai/blog/devin-annual-performance-review-2025)
- [Cognition — Coding Agents 101](https://devin.ai/agents101)
- [Microsoft Agent Governance Toolkit](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/)
- [ZenML LLMOps — Building Production AI Agents](https://www.zenml.io/llmops-database/building-production-ai-agents-lessons-from-claude-code-and-enterprise-deployments)
