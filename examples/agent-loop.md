# Real Example: One Agent Run

An end-to-end trace of a single agent run, captured live. The user prompt was:

> please update readme based on thsese contenxt. not very long but core ideas and some important points. committ and push

What follows is every iteration of the loop, in order, until the agent stopped.

## Setup

- **Harness**: Claude Code
- **Model**: `claude-opus-4-7`
- **Working directory**: `/Users/ehsan/CodingProjects/futureinfer`
- **Tools available**: `Read`, `Edit`, `Write`, `Bash`, `Grep`, `Glob`, `Agent`, …

The "context" the model sees on each iteration is the full conversation up to that point: the user's prompt, every prior tool call, and every prior tool result.

---

## Iteration 1 — read the current README

**Think.** "Before editing, I need to see what's already there so my edit anchors against real text."

**Act.** `Read` tool:

```
file_path = /Users/ehsan/CodingProjects/futureinfer/README.md
```

**Observe.** 71 lines of content: title, *Premise*, *Open Questions* (Agents, Goals, Context, Tools, Runtime, Verification, Controlled action, Evaluation), *Scope*, *Status*, *License*.

---

## Iteration 2 — check git state

**Think.** "Confirm there's a remote and the tree is clean before I start editing and committing."

**Act.** `Bash`:

```bash
git remote -v && git status
```

**Observe.**

```
origin git@github.com:FastInfer/futureinfer.git (fetch)
origin git@github.com:FastInfer/futureinfer.git (push)
On branch main
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

Decisions formed: remote is `origin`, branch is `main`, no in-progress work to worry about.

---

## Iteration 3 — edit the README

**Think.** "Insert a new *Working Definitions* section between *Premise* and *Open Questions*. Three subsections: Agent, The loop, Tools. Anchor the edit on the boundary between those two existing headings so the match is unambiguous."

**Act.** `Edit` tool:

```
old_string = "...is organized around the open questions, not around a fixed answer.\n\n## Open Questions"
new_string = "...same prefix... + new Working Definitions section + ...\n\n## Open Questions"
```

**Observe.** *"The file … has been updated successfully."*

---

## Iteration 4 — verify the edit and check commit-message style

**Think.** "Sanity-check the diff size, then look at the last few commit subjects so I match the project's style."

**Act.** `Bash`:

```bash
git diff --stat && echo "---" && git log -5 --oneline
```

**Observe.**

```
README.md | 39 +++++++++++++++++++++++++++++++++++++++
1 file changed, 39 insertions(+)
---
6bea7a2 docs: restructure README around open questions, add research notes
34d1211 docs: rewrite README to clarify the research mission, project scope, and core technical focus
41c31b2 Initial commit: add README
```

Decisions formed: prior commits use the `docs:` prefix → match it. 39 insertions, 0 deletions → no accidental removals.

---

## Iteration 5 — stage and commit

**Think.** "Use HEREDOC for the multi-line message; subject line short; body explains *why* not *what*."

**Act.** `Bash`:

```bash
git add README.md && git commit -m "$(cat <<'EOF'
docs: add working definitions for agent, loop, and tools

Grounds the open questions in a concrete picture: what an LLM agent is,
how the think-act-observe loop maps to API calls vs harness code, and
how tools are surfaced to the model at runtime.
EOF
)"
```

**Observe.**

```
[main 3391049] docs: add working definitions for agent, loop, and tools
 1 file changed, 39 insertions(+)
```

---

## Iteration 6 — push

**Think.** "User asked to push. Push to `origin/main`."

**Act.** `Bash`:

```bash
git push origin main
```

**Observe.**

```
To github.com:FastInfer/futureinfer.git
   6bea7a2..3391049  main -> main
```

---

## Iteration 7 — terminate

**Think.** "Goal achieved: README updated, committed, pushed. Reply to the user; no more tool calls needed."

**Act.** *None.* Final text response only.

**Observe.** *N/A.* The loop ends because the model emitted a response with no `tool_use` blocks.

---

## What to notice

1. **Each iteration's action was chosen *after* observing the previous result.** Nothing was planned upfront. The choice in Iteration 5 to use the `docs:` prefix was only possible because Iteration 4 actually saw the git log. If the log had used a different convention, the commit message would have been different.

2. **Only Think is an LLM call.** Iterations 1–7 each correspond to *one* call to the model. Act is plain code (`git`, `Read`, `Edit`); Observe is the harness packaging the tool's output as a `tool_result` and sending it back on the next call. So this run = **7 LLM calls + 5 tool executions** (1 `Read`, 1 `Edit`, 3 `Bash`).

3. **The model has no memory between calls.** Every iteration re-sent the entire conversation: the user's prompt, all prior tool calls, and all prior tool results. By Iteration 6 the context contained the full README, the diff stat, the recent commit log, and the new commit hash.

4. **The loop ended by emission, not by command.** The harness didn't say "stop." The model produced a response in Iteration 7 with no `tool_use` blocks, and the harness exited.

5. **Branching choices the model made.**
   - *Read first vs. blind edit.* Iteration 1 was optional; an edit could have been attempted blind. Reading first made the `old_string` anchor reliable.
   - *Verify before commit.* Iteration 4 was optional and caught nothing this run, but on a different run it could have caught a botched edit.
   - *Commit-message prefix.* `docs:` was *matched* from the log, not assumed.

6. **What a non-agent, single-shot LLM call would have looked like.** The user pastes the prior conversation into a chatbot and asks for a unified diff plus shell commands. The model must guess the existing structure, the file path, and the commit-message style — and has no way to recover from a wrong guess. No tools, no observations, no iteration.

---

## Summary

**7 iterations → 7 LLM calls → 5 tool executions → 1 commit (`3391049`) → 1 push.**

That is the loop, end-to-end, on a real task.
