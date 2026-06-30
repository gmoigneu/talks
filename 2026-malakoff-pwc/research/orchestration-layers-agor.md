---
source: "Orchestration Layers"
publisher: "Agor (agor.live)"
url: "https://agor.live/blog/orchestration-layers"
fetched: "2026-06-08"
relevance: "Closest match to the talk thesis — explicit developer-as-architect/conductor evolution, a 7-phase model, and verification reframed as an orchestration layer. Note: vendor blog (Agor), so the later phases double as product positioning."
---

# Orchestration Layers — Agor

## Core thesis
Development has shifted from being bounded by individual typing speed and mental
capacity to being bounded by the ability to coordinate multiple agents. The
future centers on developers transitioning from individual contributors to
architects who orchestrate parallel AI agents while holding vision, architecture,
and coordination.

## The seven-phase evolution model
Each phase reveals a new bottleneck and enables a new workflow.

1. **Prompt Engineering (2023–2024)** — manual context assembly via copy-paste
   between editor and chat. Bottleneck: context handoff.
2. **Early Agentic Coding (early 2025)** — agents gain tools (file access, bash,
   web/codebase search) and gather their own context.
3. **Context Engineering (mid 2025)** — agent performance depends on structured
   information architecture; treat "context like code" (versioned, cross-linked).
4. **Parallelization Chaos (fall 2025)** — devs run 5–10 parallel sessions
   (tmux/terminals/branches); cognitive overhead, not model capability, becomes
   the limit. No coordination tooling.
5. **Multi-Agent Tooling (now)** — platforms (e.g. Agor) add: git worktree
   isolation per feature, spatial board interfaces, environment awareness with
   auto port assignment, session-tree genealogy, real-time multiplayer.
6. **Agent Orchestration (emerging)** — agents coordinate via standardized
   protocols (MCP): spawn sessions, check status, share artifacts, cross-review,
   delegate subtasks.
7. **Meta-Orchestration (future)** — supervisor agents manage other agents:
   scheduled health checks across worktrees, declarative trigger chains between
   workflow zones, policy systems (cost/concurrency/resources), async delegation
   of complete feature workflows.

## Key concepts & definitions
- **Agent orchestration** — structured coordination of multiple parallel agents
  with visibility, governance, and inter-agent communication.
- **Context engineering** — curating, structuring, and versioning information
  architecture for agent consumption; context as a managed resource.
- **Spatial boards** — Figma/Miro-like visual interface mapping sessions to
  workflow zones, using human spatial memory instead of "terminal archaeology."
- **Session trees** — genealogical tracking of how agent conversations fork,
  branch, and spawn.
- **Multiplayer development** — shared real-time access to agent sessions,
  environments, and conversations.
- **Supervisor agents** — meta-level agents that manage other agents' work and
  automate operational processes.
- **Trigger chains** — declarative sequences where zone completion auto-initiates
  the next agent workflow.
- **Circuit breakers** — automated containment that pauses orchestration when
  error rates or cost thresholds are exceeded.

## Frameworks & models

**Coordination problem hierarchy**
- Individual agent capability (solved)
- Single-session workflows (solved)
- Parallel session management (solved with multi-agent tooling)
- Inter-agent coordination (emerging)
- Autonomous meta-orchestration (future)
- Runaway mitigation (prerequisite for maturity)

**Policy systems for containment** — token budgets (API cost caps), concurrency
limits, resource caps (env/container), circuit breakers (error-rate thresholds).

**Developer role evolution**
- Phase 1–2: individual coder
- Phase 3–4: code + context architect
- Phase 5–6: conductor / orchestrator
- Phase 7: hypervisor / systems designer

## Concrete examples & patterns

**Single-prompt multi-agent workflow** — "Implement dark mode" cascades through:
planner (task breakdown + spawn) → parallel feature agents → supervisor
(scheduled testing) → review agent (consistency on test success) → test agent
(conditional if coverage drops) → docs agent (on approval) → integration
supervisor (full build) → PR agent (summary + reviewer tagging) → human review.
One human prompt; human review only at the end; intermediate work automated and
supervised.

**Supervisor agent on a schedule** — hourly across idle worktrees: verify running
environments, run validation (`pnpm check`), auto-fix or escalate, move completed
work through zones, run browser verification (Playwright MCP).

**Git worktree architecture** — each parallel feature gets an isolated worktree;
dozens of simultaneous branches without merge hazards, single repo state.

## Notable observations & quotes
- Devs discovered they "can just open another terminal," but lacked tooling to
  manage the resulting chaos.
- Agent output quality jumped — "code looks nothing like the terrible slop from a
  few months ago."
- "agentic coding tools got too good to use just one at a time, but we had no
  structure to orchestrate these agents."
- Development reimagined as a "queued, asynchronous workflow" — submit tasks, let
  them run in the background, review later.
- MCP (launched Nov 2024) reached broad adoption (OpenAI Mar 2025, Google
  DeepMind Apr 2025), thousands of production servers — "production-ready" agent-
  to-agent plumbing.

## Takeaways for the ADLC talk
1. **Spec-to-execution separation** — humans give vision + requirements; agents
   execute in parallel under automated supervision.
2. **Verification as an orchestration layer** — QA moves from manual testing to
   autonomous supervisor agents validating against criteria before human review.
3. **Human role redefinition** — from hands-on implementation to defining
   workflows, setting policies, and final verification of complex decisions.
4. **Coordination infrastructure is as critical as application architecture.**
5. **Containment is a prerequisite** — meta-orchestration needs policy systems to
   prevent runaway chains and unbounded cost.
6. **Near-linear velocity scaling** — more agents/concurrency/autonomous
   verification without proportional human oversight.
7. **Multiplayer** — same infra supports solo orchestrators and teams of humans
   coordinating teams of agents.

## Connections to this talk
- Provides the **arc spine**: a concrete role-evolution ladder
  (coder → context architect → conductor → hypervisor) for the "The shift" section.
- **Verify & Validate**: supervisor agents + circuit breakers + policy systems are
  the verification pillar made operational.
- Pairs with [[agent-harness-engineering-addyosmani]]: Osmani = the *single*-agent
  harness (model + scaffolding); Agor = *multi*-agent orchestration on top. Both
  land on: the developer's deliverable is the system around the agents, not the code.
- Caveat for honesty (per presentation-rules "mentor not marketer"): this is a
  vendor post; cite the phase model and concepts, but don't present Agor's product
  phases as settled industry fact.
