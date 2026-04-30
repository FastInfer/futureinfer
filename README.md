# FutureInfer

Open-source research on the software substrate around foundation models. Early-stage project of FastInfer Inc.

## Premise

Open-source foundation models are improving fast. The infrastructure that turns a model into something that gets work done is not. We don't yet know what the right shape of that infrastructure is. FutureInfer is organized around the open questions, not around a fixed answer.

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
