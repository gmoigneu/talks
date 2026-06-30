---
source: "Agent Harness Engineering"
author: "Addy Osmani"
url: "https://addyosmani.com/blog/agent-harness-engineering/"
fetched: "2026-06-08"
relevance: "Core support for the developer-as-architect thesis — the architect designs the harness (specs, tools, verification loops), not just the code."
---

# Agent Harness Engineering — Addy Osmani

## Core thesis
A coding agent's effectiveness derives equally from its underlying model and the
engineered systems around it. A decent model with a great harness beats a great
model with a bad harness. The substantive engineering work is harness design —
the prompts, tools, infrastructure, and feedback loops that enable autonomous
execution — not model selection.

## Definition: agent harness engineering
"Agent = Model + Harness. If you're not the model, you're the harness." Harness
engineering treats operational scaffolding as a primary artifact, not config
detail. The discipline systematically converts agent failures into permanent
constraints and rules so the system never repeats the same mistake twice.

## Key concepts & definitions

**Harness components**
- System prompts and skill files (`AGENTS.md`)
- Tools, MCP servers, and their schemas
- Sandboxed infrastructure (filesystem, bash, browser)
- Orchestration logic (subagent spawning, handoffs)
- Hooks and middleware (execution enforcement)
- Observability infrastructure (logging, tracing, metering)

**ReAct loop** — Reason → Action (tool call) → Observe → Repeat. The harness
designs both the available tools and the loop's control flow.

**Context rot** — model performance degrades as the context window fills.
Addressed via compaction (summarize/offload older context), tool-call offloading
(keep large outputs on the filesystem), and progressive skill disclosure.

**The ratchet pattern** — every documented agent failure becomes an enforced
rule. Rules trace back to specific failures, not hypothetical concerns: "each
line in a good `AGENTS.md` should be traceable back to a specific thing that went
wrong."

**Skill-issue reframe** — agent failures stem mostly from configuration gaps,
not model limits. HumanLayer: most failures are "skill issues," correctable
through harness adjustment rather than waiting for better models.

**Planner / Generator / Evaluator pattern** — separating evaluation into a
distinct agent prevents self-evaluation bias; models "reliably skew positive when
grading their own work," so independent verification is more reliable.

**Sprint contract** — generator and evaluator agents negotiate success criteria
before work begins, reducing scope drift.

**Compaction** — near context limits, the harness summarizes and offloads older
sessions to the filesystem to keep going.

**Ralph loops** — multi-session autonomous execution where a hook intercepts
completion attempts and re-injects the original prompt into a fresh context
window; each iteration reads prior state from the filesystem but starts with
clean reasoning.

## Frameworks & principles

**Behavior-driven harness design** — reverse the process: desired behavior →
derive the harness components that enable it.
- Durable work → filesystem + Git
- Code execution → bash + sandboxes
- Memory across sessions → `AGENTS.md`, web search, MCPs
- Long-horizon tasks → planning, verification, Ralph loops
- Safety → sandboxes, allow-listing, pre-commit hooks

**The `AGENTS.md` standard** — a markdown rulebook injected into every system
prompt. Keep under ~60 lines (a pilot's checklist, not a style guide); earn each
line through specific failure history; capture conventions (package manager, test
framework, forbidden commands, logging standards).

**Tool design** — quality over quantity (10 focused tools beat 50 overlapping);
concise, clear descriptions compete for attention; tool descriptions populate
prompts, so MCP servers are trusted input (a security concern).

**Hook pattern** — enforcement scripts at lifecycle points (before tool calls,
after edits, pre-commit). "Success is silent, failures are verbose."

**Sandbox strategy** — isolate execution; ship defaults (runtimes, Git, test
CLIs, headless browsers); allow command allowlisting, network isolation,
on-demand spin-up.

**Model–harness training loop** — useful harness primitives get standardized,
then absorbed into the next model's training, improving capability. Models become
specifically strong at harness-enabled actions (filesystem, bash, planning,
subagent dispatch) rather than staying genuinely general.

## Concrete examples & case studies

- **Terminal Bench 2.0**: Viv Trivedy's team moved an agent from 30th → 5th by
  changing only the harness, keeping the model constant (Claude Opus 4.6) —
  better codebase-tailored tools, tighter prompts, sharper back-pressure.
- **Claude Code architecture** (most mature public harness reference): input
  layer (UI, sessions, permission gates), knowledge layer (skill registry,
  context compression, task graph, memory), integration layer (MCP runtime),
  execution layer (tool dispatch, streaming, prompt caching), output layer,
  observability (event bus, background execution), multi-agent coordination
  (subagents, mailboxes, worktree isolation).
- **Convergence**: Claude Code, Cursor, Codex, Aider, Cline show increasingly
  similar harness patterns despite different models — convergence on load-bearing
  scaffolding over model differentiation.

## Notable quotes & stats
- "A decent model with a great harness beats a great model with a bad harness."
- "it's not a model problem. It's a configuration problem." (HumanLayer)
- "good agent building is an exercise in iteration. You can't do iterations if you
  don't have a v0.1." (Viv Trivedy)
- "Compaction alone wasn't sufficient" for long-horizon tasks — sometimes full
  context resets with structured hand-offs are needed. (Anthropic)
- "every component in a harness encodes an assumption about what the model can't
  do on its own." (Anthropic)

## Takeaways for the ADLC talk
1. Model selection is secondary; the harness determines capability.
2. Failure-driven design (ratchet) builds resilience without model upgrades.
3. The gap between model capability and output is mostly a harness gap.
4. Improving the harness beats waiting for next-gen models.
5. Harnesses evolve *with* models, not backward — better models raise the ceiling.
6. Harness-as-a-Service is emerging (Claude Agent SDK, Codex SDK, OpenAI Agents
   SDK): customize domain prompts/tools, not the fundamentals.
7. Open direction: dynamic, just-in-time assembly of tools and context.

## Connections to this talk
- **Developer-as-architect**: the architect's deliverable is the harness — specs
  (`AGENTS.md`), tools, sandboxes, and verification loops — not hand-written code.
- **Specify**: `AGENTS.md` + the ratchet pattern = the spec as living, failure-
  earned source of truth.
- **Verify & Validate**: planner/generator/evaluator separation and "success is
  silent, failures are verbose" map directly onto the verification pillar.
