# FutureInfer

Open-source research on the software substrate around foundation models. Early-stage project of FastInfer Inc.

## Premise

Open-source foundation models are improving fast. The infrastructure that turns a model into something that gets work done is not. We don't yet know what the right shape of that infrastructure is. FutureInfer is organized around the open questions, not around a fixed answer.

## Working Definitions

Shared vocabulary so the open questions below land on the same target.

### Agent

> A system built around a language model that, given a goal in natural language, runs in a loop — reasoning over its context, calling tools to act on an environment, and feeding the results back — until the goal is met or abandoned.

This excludes a single LLM completion, a RAG pipeline with no actions, or a fixed workflow that calls an LLM at one step. In each of those, the model is not the thing choosing what to do next.

Defining pieces:

- **LLM as policy** — the model decides each next step; no hand-coded controller.
- **Natural-language goal** — a prompt, not a reward function or formal spec.
- **Tool use** — real side effects on a real environment, not just text.
- **Closed loop** — each action is chosen *after* observing the previous result.
- **Context as state** — memory is the conversation, scratchpad, and files the model can read.
- **Autonomy across steps** — the human sets the goal; the agent picks intermediate actions.

### The loop

One iteration = one LLM call + tool execution(s) + message bookkeeping.

- **Think** — LLM call. The model emits reasoning text *and* structured tool requests in a single response.
- **Act** — the harness parses the tool request and runs the actual tool. No LLM involved.
- **Observe** — the harness appends the tool's output to the conversation as a `tool_result`. No LLM involved.

The model has no memory between calls; every iteration re-sends the full growing history. The loop ends when the model returns a response with no tool requests.

### Tools

Tool *use* is a general capability learned in training. Specific tools are not baked into the weights — they are passed as JSON schemas in each API call, and the model picks them up from name, description, and input shape.

Adding a tool means writing a schema and an executor; no fine-tuning required. MCP (Model Context Protocol) is the standard plug-in mechanism. Performance degrades as the tool list grows, so production systems gate which tools are loaded per call.

---

This is the *current* picture. The open questions below are about how much of it survives contact with harder problems.

## Open Questions

The repository treats each of these as a research thread. An answer — partial, experimental, or critical — can become a project, a prototype, or a contribution.

### Agents

- What is an agent, beyond a model in a loop? What separates an agent from a script?
- When should a system be one agent vs. many cooperating agents?
- How does an agent know when it is done, stuck, or wrong?

### Goals and intent

- How should a human specify a goal so that a machine can act on it without misreading it?
- What acceptance criteria can be inferred, and what must be stated?
- How is intent revised mid-task without losing prior work?

### Context and memory

- What belongs in the model's context at each step, and what does not?
- What should persist across sessions, and in what form — traces, facts, skills, embeddings, code?
- How is stale or wrong memory detected and removed?

### Tools and protocols

- What is the right interface between a model and a tool?
- How are tools described, discovered, composed, and versioned?
- How do tool failures propagate without derailing the system?

### Runtime and sandboxing

- What execution guarantees does an agent runtime need to provide?
- What isolation primitives are missing for safe tool execution?
- How is resource use — time, money, network, disk — bounded?

### Verification

- How do we know an agent's output is correct before acting on it?
- Where do tests, type checks, secondary models, and human review each fit?
- What can be verified cheaply, and what cannot be verified at all?

### Controlled action

- What makes an action reversible, and what makes it durable?
- How is authorization scoped, requested, and revoked?
- What audit trail is needed for an agent that touches shared systems?

### Evaluation

- How do we measure whether an agent is improving?
- What benchmarks exist, and what do they fail to capture?

## Scope

Not a chatbot, IDE plugin, automation script, or assistant wrapper. A research substrate.

## Status

Early stage. Questions, prototypes, and counter-arguments are welcome.

## License

See repository.
