# Open-Source Agent Frameworks

Map of the agentic-software landscape as of April 2026. Star counts are approximate and change weekly.

## Landscape

| Project | ~Stars | Position |
|---|---|---|
| OpenClaw | 210k–300k+ | Local-first personal assistant |
| n8n | 180k | Workflow automation w/ AI |
| Dify | 130k | Low-code visual agent builder |
| Open WebUI | 124k | Self-hosted LLM UI |
| LangChain | 95k | Generic agent toolkit |
| OpenHands (ex-OpenDevin) | 70k | Coding-specific agent |
| RAGFlow | 70k | RAG pipelines |
| AutoGen | 55k | Multi-agent (now in maintenance, merged into MS Agent Framework) |
| CrewAI | 44k | Role-based multi-agent |
| LangGraph | 25k | Stateful orchestration, human-in-the-loop |
| Mastra | 21k | TypeScript-first |
| OpenAI Agents SDK | 19k | Lightweight, multi-provider |
| Google ADK | 18k | Google Cloud-native |

## Notable case: OpenClaw

By Peter Steinberger, first published Nov 2025. ~9k → 210k+ stars in roughly two weeks. MIT-licensed, Node.js/TypeScript, pnpm monorepo.

What it is:

- Local-first personal AI assistant — runs on the user's own machine
- Memory stored as Markdown files on disk (not a vector DB)
- Reaches users via existing channels (WhatsApp, Telegram, Slack, Discord, Signal, iMessage, Google Chat)
- Heartbeat daemon — agent acts autonomously on a schedule, not just on prompts
- Companion apps for macOS / iOS / Android with voice wake
- Security defaults: DM pairing for unknown senders, sandboxed sessions for group channels

What it is not: a toolkit. It is an opinionated, integrated product — sidesteps the framework debate.

Hypotheses for the star velocity (not proven):

1. Markdown memory is greppable, git-able, user-owned.
2. Meets users on existing platforms — no new UI to learn.
3. Heartbeat makes it feel like an assistant, not a chat session.
4. Local-first / privacy story.
5. Founder reach (Steinberger / PSPDFKit).

## Quick takes on the others

- **LangChain / LangGraph** — generic toolkit. LangGraph adds stateful orchestration and is what most enterprise users settle on. Production case studies: Klarna, Uber, LinkedIn.
- **OpenHands** — coding-specific, sandboxed Docker workspace, ~53% on SWE-bench Verified with strong models. Has a published Software Agent SDK paper ([arxiv 2511.03690](https://arxiv.org/html/2511.03690v1)).
- **AutoGen** — multi-agent conversations. Now in maintenance, merged into Microsoft Agent Framework. Worth understanding what was kept vs discarded.
- **CrewAI** — role-based, "minimal code for agent setup." Less control over state and execution flow.
- **Dify / n8n** — visual, low-code. Hit highest star counts because the audience is non-developers.
- **OpenAI Agents SDK** — deliberately lightweight, multi-provider. Newer, limited production documentation.
- **Mastra** — TypeScript-first, fills the JS gap.

## Threads to go deeper

- [ ] Read the OpenClaw runtime source. How is the heartbeat scheduled? What gates an autonomous action?
- [ ] OpenHands Software Agent SDK paper ([arxiv 2511.03690](https://arxiv.org/html/2511.03690v1)) — extract the architectural primitives they consider production-grade.
- [ ] AutoGen → Microsoft Agent Framework migration: what was kept, what was discarded, why?
- [ ] LangGraph human-in-the-loop primitives — where is the actual interruption mechanism in the code?
- [ ] Why did Dify and n8n hit 130k–180k on the *low-code* axis but no *substrate* project has? Is the demand asymmetric, or has nobody shipped a credible substrate?
- [ ] Per-framework verification story: does each one have *any* first-class verification primitive? If not, what does the user wire up?

## Sources

- [openclaw/openclaw](https://github.com/openclaw/openclaw)
- [OpenClaw — Wikipedia](https://en.wikipedia.org/wiki/OpenClaw)
- [What Is OpenClaw? — Milvus blog](https://milvus.io/blog/openclaw-formerly-clawdbot-moltbot-explained-a-complete-guide-to-the-autonomous-ai-agent.md)
- [OpenHands](https://openhands.dev/)
- [Best Open Source Agent Frameworks 2026 — Firecrawl](https://www.firecrawl.dev/blog/best-open-source-agent-frameworks)
- [Top 20 GitHub AI Agent Repos 2026 — Fungies.io](https://fungies.io/top-github-repositories-ai-agent-frameworks-2026/)
