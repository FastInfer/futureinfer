# Failure Modes

Academic taxonomies of how LLM agents fail. The most defensible references because they are systematic surveys, not opinion.

## MAST — Multi-Agent System Failure Taxonomy

**Source:** [arxiv 2503.13657](https://arxiv.org/abs/2503.13657)

1,600+ annotated execution traces across 7 popular multi-agent frameworks. First systematic taxonomy of MAS failures.

Key finding: failures cluster into specification, inter-agent misalignment, and verification gaps. **Verification is the least-addressed category across all 7 frameworks studied.**

## System-level taxonomy (15 failure modes)

**Source:** [arxiv 2511.19933](https://arxiv.org/abs/2511.19933)

15 hidden failure modes in real-world LLM applications. Confirmed examples:

- Multi-step reasoning drift
- Latent inconsistency
- Context-boundary degradation
- Incorrect tool invocation
- Version drift
- Cost-driven performance collapse

(The remaining 9 still need to be extracted from the paper — see threads below.)

None are addressed by current frameworks as first-class concerns.

## SWE-bench failure analysis

**Source:** [arxiv 2503.12374 — "Understanding Why AI-driven Code Agents Fail at GitHub Issues"](https://arxiv.org/pdf/2503.12374)

Empirical breakdown of why coding agents fail:

- **52%** of unresolved tasks: incorrect or overly-specific implementation — agents produce code that does not address the issue or does not generalise.
- **23.4%**: cascading failed edits — one bad edit poisons subsequent ones.
- **~75%** failure rate on environment-level errors (OSError, DB integrity).
- Most failed trajectories **do** locate the right file. Fault is at deeper levels (semantic, algorithmic), not retrieval.

Implication: the missing piece is verification + recovery, not better retrieval.

Model-specific patterns:

- Strongest models (GPT-5, Opus 4.x) — instruction-following on long, nuanced specs.
- Weaker models — tool use, syntax errors, premature termination.
- Edits remain the most-failed tool call across all models.

## How LLMs fail in agentic scenarios

**Source:** [arxiv 2512.07497](https://arxiv.org/pdf/2512.07497)

Qualitative analysis of 900 execution traces across 3 representative models. Key finding: **model scale alone does not predict agentic robustness**.

- Llama 4 Maverick (400B) only marginally better than Granite 4 Small (32B) on uncertainty-driven tasks.
- DeepSeek V3.1's reliability comes from post-training RL, not scale.

Implication: throwing parameters at the problem does not fix agentic reliability.

## Where LLM agents fail and learn from failures

**Source:** [arxiv 2509.25370](https://arxiv.org/pdf/2509.25370)

Direct claim: existing LLM agents lack the reliability required for real-world deployment. Errors range from misinterpreting instructions, to misusing tools, to breaking down in long-horizon reasoning.

## Memory survey

**Source:** [arxiv 2404.13501 — "A Survey on the Memory Mechanism of Large Language Model based Agents"](https://arxiv.org/abs/2404.13501) (now published in ACM TOIS)

Open problems explicitly named:

- Separation of memory types (episodic vs semantic vs procedural)
- Lifetime management — what to keep, what to forget
- Error propagation from "misaligned experience replay"
- Lack of adaptive prioritisation / forgetting strategies
- Multi-agent memory coordination

Companion benchmark for very-long-term memory: [arxiv 2402.17753](https://arxiv.org/abs/2402.17753) ([snap-research.github.io/locomo](https://snap-research.github.io/locomo/)).

## Threads to go deeper

- [ ] Extract all 15 failure modes from arxiv 2511.19933 with one concrete example each.
- [ ] Map MAST taxonomy categories against the 7 frameworks studied — which categories does each framework leave unaddressed?
- [ ] SWE-bench failure modes by model size — does failure shape change at scale, or does it just shrink uniformly?
- [ ] Cross-reference: which failure modes are runtime-addressable (sandboxing, verification harness) vs model-addressable (better post-training)?
- [ ] LoCoMo benchmark — what specific long-term memory failures does it surface?
- [ ] Read [arxiv 2507.21504 "Evaluation and Benchmarking of LLM Agents: A Survey"](https://arxiv.org/html/2507.21504v1) and extract the methodology gaps for production-readiness measurement.

## Sources

- [Why Do Multi-Agent LLM Systems Fail? — arxiv 2503.13657](https://arxiv.org/abs/2503.13657)
- [Failure Modes in LLM Systems — arxiv 2511.19933](https://arxiv.org/abs/2511.19933)
- [Understanding Why AI-driven Code Agents Fail — arxiv 2503.12374](https://arxiv.org/pdf/2503.12374)
- [How Do LLMs Fail in Agentic Scenarios — arxiv 2512.07497](https://arxiv.org/pdf/2512.07497)
- [Where LLM Agents Fail — arxiv 2509.25370](https://arxiv.org/pdf/2509.25370)
- [Memory Mechanism Survey — arxiv 2404.13501](https://arxiv.org/abs/2404.13501)
- [LoCoMo — arxiv 2402.17753](https://arxiv.org/abs/2402.17753)
- [Evaluation and Benchmarking Survey — arxiv 2507.21504](https://arxiv.org/html/2507.21504v1)
