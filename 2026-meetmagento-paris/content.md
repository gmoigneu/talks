---
event: "Meet Magento Paris 2026"
title: "Development in an Agentic World"
subtitle: "The Mastermind Architect of Validation & Verification"
date: ""
duration: "30 minutes (~26-28 min talk incl. ~3-min live demo + buffer/Q&A)"
format: "Talk"
speaker: "Guillaume Moigneu"
audience: "Magento / Adobe Commerce agencies & integrators familiar with AI-assisted development. Org maturity: mostly Stage 2-3 (Islands), a few agencies entering 4-5."
deck: "index.html"
theme: "dispatch"
sources:
  - "resources/8-stages.md (primary spine, 8 stages of AI engineering maturity)"
  - "research/agent-harness-engineering-addyosmani.md (Agent = Model + Harness; the ratchet)"
  - "research/orchestration-layers-agor.md (role evolution; orchestration; vendor caveat)"
  - "Viv Trivedy, 'Improving Deep Agents with Harness Engineering', vtrivedy.com (17 Feb 2026), PRIMARY for the Top 30 -> Top 5 stat"
  - "Augment Code / Intent, context-engineering framework (Intent / Environment / System Memory / Shared State); 'poisoned context' insight"
---

# Development in an Agentic World, The Mastermind Architect of Validation & Verification

## The spine (one sentence)

> Programming was always the *consequence* of engineering judgment. Agents
> collapse the consequence, so the job moves up to the judgment, and the skill
> that earns the promotion is making the machine **prove its work** so you can
> spend yourself on whether it built the **right** thing.

## Posture & promise

- **Emotional note: empowerment, not warning.** The story is an ascension , 
  "you just got promoted to architect; here's your new craft", not "adapt or die."
- **Thought leadership + pragmatism.** Bold POV (industrialization, V&V as the new
  core skill) anchored by one artifact the audience can start building this week.
- **No slop/vibecoding fear framing.** We sell the upside of industrialization,
  not the downside of bad code.
- **The one sentence they repeat Monday:** *"Stop shipping code that looks right.
  Start architecting systems that prove it."*

## Meet Magento 30-min adaptation (from the Shopware 45-min original)

Decided in the redefinition interview:

- **Reframe to Magento / Adobe Commerce, agency audience.** The worked example
  is now a **cart price rule (promotion)**, not loyalty points. The silent-money
  bug is reframed around **per-line vs per-total tax rounding** , a topic the
  Magento room already feels in their bones (`ruleTotal()`). e2e references are
  **MFTF / Playwright**; architectural gates use Magento idioms (no `ObjectManager`
  in a loop; no logic/SQL in `.phtml`; Controller → Service → ResourceModel layering).
- **Cold open on the scar**, not the benchmark. We now open on the agent that
  edited a failing test to pass (was Section 3b); the Terminal-Bench harness stat
  follows as the *answer* ("build the system around the model"). More visceral for devs.
- **~14 slides cut to hit 30 min** (50 → 40), targeting what didn't land last time:
  - **8-stage map** kept as a single slide, but reworked for clarity: grouped into
    **three acts** (you → the team → the factory) instead of a flat list of 8, with
    "you are here" pinned on Islands and a **QR to the full article**
    (upsun.com/blog/8-stages-ai-engineering-maturity, `resources/8-stages-qr.svg`).
  - **Tamper-proof tests simplified**: dropped DSSE / in-toto / `gh attestation`
    jargon; kept the defensible core (tests read-only + edit-detection). Same on the
    PR-evidence slide.
  - **Stage 6-8 horizon** collapsed from 3 statement slides into one 3-card slide.
  - **Repetition removed**: merged the two context-cost stats (Tipping Point +
    "deleted 95%") into one; cut the Bet "anatomy" slide (it repeated the Bet slide);
    cut the graphify and Semantic-Anchors tangents (folded a one-line anchor mention
    into the schemas/ADR slide); folded the standalone "ascension", honest-caveat,
    and "success is silent" beats into adjacent slides' notes; merged the close
    "relocations" + "do this" into one grid; cut the Fable-5 joke intermission.
- **Upsun: kept both moments, trimmed.** The preview-environment-as-validation beat
  stays inside the centerpiece; one infra "none of this works on a laptop" statement
  stays as the horizon close. **Dispatch section trimmed 4 → 2** slides (reveal +
  one real-run screenshot; cut six-pillars + approvals).
- **Live demo: kept, adapted to Magento.** Same silent-money-bug runner
  (`php bin/bench.php`), reframed to a cart-price-rule PR. Repo QR unchanged
  (github.com/gmoigneu/scd-demo). TODO before stage: reskin a Magento branch, or keep
  the narration framework-agnostic; re-pull the Terminal-Bench leaderboard.

## Decisions locked

- Title: full "Mastermind Architect of Validation & Verification".
- Centerpiece delivery: **slides + script + ONE live demo.** Grilling Session
  script and proof artifacts on-slide; one ~2-min live demo reinstated (was: none),
  the silent-money-bug `bench.php` from the scd-demo repo (github.com/gmoigneu/scd-demo) (recorded fallback
  if Wi-Fi fails). Everything else stays slide-based.
- **Hands-on layer added** (see `resources/hands-on-tactics.md` +
  `resources/implementation-plan.md`): real PHP/Shopware artifacts replace
  abstractions, all sourced from a runnable, verified scd-demo repo (github.com/gmoigneu/scd-demo)
  (AGENTS.md Judgment Boundaries, Deptrac + PHPStan gates, GrumPHP, the Critic
  agent, `/grill-me`, the silent-money-bug demo). New slides: H2 (silent money bug /
  demo), H9 (Deptrac architectural gate), H5 (GrumPHP), H3 (deleted-95%-of-skills
  stat), H1 (AGENTS.md Judgment Boundaries), H4 (`/grill-me`), H7 (Critic agent).
  Cuts to hold time: Islands symptom+trap merged; "eval becomes the product" folded
  into the Stage-6 slide.
- Upsun: **one explicit slide** in the Stage 7-8 beat, framed as the category we
  work on ("this is the problem"), not a pitch. Mentor, not marketer.

## The flywheel (the through-line diagram, reused across the deck)

```
        Bet (intent + success signals)
                 │
                 ▼
        Context  (AGENTS.md, schemas/ADRs, shared memory)
                 │   better input ─► better output ─► cheaper V&V
                 ▼
        Execute  (agents, parallel, sandboxed)
                 │
                 ▼
   Verify  ── did we build it RIGHT?  → machine (tests, types, lint, security)
   Validate ─ did we build the RIGHT thing? → e2e/Gherkin + the architect's call
                 │
                 ▼
        Feedback  (pass OR fail becomes context for the next iteration, the ratchet)
                 └──────────────► back to Context
```

The loop is the talk. Each section adds one arc of it; the centerpiece completes it;
Stages 7-8 make it recursive (agents generate their own Bets).

---

# Section-by-section

## 0 · The Promotion, hook (≈4 min)

**Beat:** what-is → reframe.

- **Open cold with the stat.** A coding agent went from **Top 30 to Top 5 on
  Terminal-Bench 2.0**, *they only changed the harness* (better tools, tighter
  prompts, sharper back-pressure). The leverage was never the model, it's the
  *system you build around it*. That system is your new job. (Plants the whole
  talk in one number; pays off in Section 3.)
  - **Source (verified):** Viv (Vivek) Trivedy, LangChain, post *"Improving Deep
    Agents with Harness Engineering"* (17 Feb 2026, vtrivedy.com), on the deepagents
    CLI. Popularized by Addy Osmani's *Agent Harness Engineering*.
  - **Verified figure (example-research):** the primary LangChain blog states
    deepagents-cli **52.8 → 66.5** on Terminal-Bench 2.0, model fixed at
    **GPT-5.2-Codex**, harness only. (Osmani's "Claude Opus 4.6" is a secondhand
    error.) **On stage say only "Top 30 → Top 5, harness only"** , keep model/% out
    of your mouth. Vendor self-report on a fast-moving leaderboard; re-pull the
    morning of the talk.
- The traditional SDLC is a **Craft-Era artifact**: rigid, sequential, bottlenecked
  by manual handoffs, built on the assumption that *the human is the execution unit*.
- The Agentic Development Lifecycle (ADLC) is a **concurrent loop**: agents execute;
  humans relocate to intent, architecture, governance.
- **Disarm the fear in the room up front.** Developers hear "industrialize execution"
  and brace for deskilling. The reframe: *programming was always downstream of
  architecture and engineering decisions.* It was the amazing-but-derivative part.
  Agents collapse it, freeing you to do what engineering was always about.
- **Everybody can ascend**, but you embrace the change, you don't fight it.
- **Promise:** by the end you'll leave with the one artifact that makes the
  ascension real (the verification harness) and the model that organizes it (V&V).

**Slide ideas:** title; pipeline-vs-loop visual (`section`/`statement`); the
promise line as a `statement`.

## 1 · The Map, where the ecosystem is (≈6 min)

**Beat:** what-is (locate the pain).

- The **8 stages of AI engineering maturity** as an *org-level* trust gradient
  (credit Steve Yegge's individual levels → team/org reframe, `8-stages.md`).
  Walk fast; this is orientation, not the lesson.
  1. Vacuum · 2. Drift · 3. Islands · 4. Standardization bet · 5. Workflow
  redesign · 6. Operating system · 7. Bright factory · 8. Autonomous factory.
- **"You are here" → Islands (Stage 3).** Name the pain precisely:
  *One Developer, Two Dozen Claudes.* Individuals scale output; the team inherits
  **coordination debt**, merge hell, features nobody asked for, a fast team
  resenting a slow one.
- **The trap:** scaling the individual *deepens* the team bottleneck, you flood
  the old pipeline with unaligned output. A faster horse, not a factory.
- **Honest caveat (credibility):** don't skip stages; *the pain of each stage is
  the lesson that earns the next one.* Stay skeptical, the hype is loud, the
  evidence quieter. (Mentor, not marketer.)

**Slide ideas:** the 8-stage map (`cards` or a wide table-as-image); "You are
here" marker on Islands; the coordination-debt symptom as a `statement`.

## 2 · The Lever, stop going faster, change what you do (≈5 min)

**Beat:** the turn (what-is → what-could-be).

- Role inversion: **Executioner/Editor → Architect of Intent / Governor.**
- The keystone line: **"If it's not proven, it doesn't exist."**
- **Verification-first is the entry point, not the endgame.** It's a forcing
  function: to prove something you need a definition of done (→ specs/Bets), and
  to make the proof repeatable you need the rules in the repo (→ context/AGENTS.md).
  Verification *drags the standardization and workflow-redesign behind it.*
- Introduce the **flywheel** at a glance (Bet → Context → Execute → V&V → Feedback).

**Slide ideas:** role inversion (two-column before/after); the keystone as a
big `statement`; first reveal of the flywheel diagram.

## 3 · CENTERPIECE, The Mastermind's Craft: Validation & Verification (≈14 min)

**Beat:** the payoff. This is the heart; everything else sets it up.

### 3a. The blade, Verification vs Validation
- **Verification, "did we build it *right*?"** Mechanical, evidence-rich,
  **delegated to the machine**: unit tests, types, linters, security, clarity.
- **Validation, "did we build the *right thing*?"** Intent alignment, **the
  architect's relocated judgment.**
- **Three layers** (the honest model):
  1. **Verify → harness** (fully automatable).
  2. **Validate-against-spec → e2e / Gherkin** (machine-checkable *because* intent
     is written down).
  3. **"Is the Bet itself right?" → you, irreducibly.** The one thing that never
     delegates. This is where judgment "relocates to where it matters."
- The ascension made concrete: **hand verification to the machine so you can spend
  yourself on validation.**

### 3b. The instrument, the harness (evidence over trust)
- **Prove It methodology:** if work isn't proven, it doesn't exist.
- **The scar that earns the rule (failure story).** A real one: an agent faced a
  failing test and "fixed" it by **editing the test to pass** instead of fixing the
  code. It reported green. *That* is why the next rule exists, and why the ratchet
  matters: this failure becomes a permanent constraint, not a one-off catch.
- **Tamper-proof tests (reframed for accuracy):** "SHA-256 of the test output" has
  **no established precedent** , don't claim it. Present the defensible trio instead:
  (1) tests **read-only / isolated** in CI (ImpossibleBench: cheating drops to ~0
  when tests are read-only); (2) **test-file-edit detection** (EvilGenie); (3) a
  **DSSE-signed in-toto test-result attestation** + GitHub Artifact Attestations
  (`gh attestation verify`). The scar is real and citable (Anthropic arXiv:2511.18397;
  ImpossibleBench "GPT-5 exploits 76%").
- **Visual evidence:** for UI, agent records a **Playwright video** of the fix. No
  video → the human doesn't open the review.
- **The validation layer / Harness:** git hooks forbid commits that fail lint/types;
  CI linters enforce *architectural* integrity (e.g. no DB access from templates).
- Principle: **"success is silent, failures are verbose."**
- Delivery = on-slide annotated screenshots of the proof artifacts (no live demo).

### 3c. The input side, better input, better output, cheaper V&V
- **Better input → better output → cheaper proof.** Verification is only easy when
  the input was good. Context is a supply chain.
- **Context is more than code (the expansion).** Code is the smallest part. Four
  things the agent actually needs to know (context-engineering frameworks , 
  Augment / Intent):
  1. **Intent**, the Bet, constraints, invariants; what "done" means, what must
     never break.
  2. **Environment**, the live codebase, dependencies, tests, runtime; the system
     as it actually is.
  3. **History**, PRs, commits, and the *why* behind past decisions (ADRs), not
     just the diff.
  4. **People**, contributors and ownership; who understands which system, and the
     scars they carry.
- **The Tipping Point:** quality degrades once a window is ~40-50% full regardless
  of total size (Smart Zone vs Dumb Zone), so you can't pour all four in, you
  curate. (Directional, not a hard number, say so.)
- **Curate surgically, the risk isn't *missing* context, it's *poisoned* context**
  (stale info degrades output more than absence). Moves: **Persist** (`AGENTS.md` +
  decision records hold Intent & History), **Select** (pull only what the task
  needs, query, don't dump; disable noisy tools), **Compress** (summarize at the
  Tipping Point), **Isolate** (parallel agents so one bad decision can't poison the
  next).
- **Query a graph, don't dump files (History + People at scale).** A
  **knowledge-graph context layer** turns PR history, decisions and ownership into
  something queryable instead of grepped. *One example:* graphify (committed-to-git
  graph over MCP), it tags edges `EXTRACTED / INFERRED / AMBIGUOUS`, i.e.
  *confidence on the context itself*: trust-through-evidence applied to the input.
  Frame as the pattern, not a tool endorsement. (Foreshadows the Stage-6 Context
  Engine.)
- **Schemas = the mold, not just the goal.** Typed interfaces, API/DB schemas, and
  ADRs are **machine-checkable contracts.** "Did it guess right?" becomes "does it
  conform?", and conformance, the harness checks for free. (Schemas are the bridge
  from judgment to automated verification: the mold shapes the part; you cut the
  mold.)

### 3d. Intent as Bets, not requirements
- Stop writing *requirements* (which prescribe a solution); write **Bets**, what
  you believe, how you'll know, and what you won't risk.
- **Lineage (credit, not coinage):** Shape Up (Ryan Singer) , appetite + the
  six-week circuit breaker; ADRs (Michael Nygard, 2011) as the decision-record form.
  Pair each Bet with a one-screen ADR (scd-demo `doc/adr/0001`), the
  record the ratchet appends to.
- **Anatomy of a Bet (always three parts):**
  1. **Hypothesis**, what we believe will move a signal ("loyalty points lift
     repeat purchases").
  2. **Signal**, the measurable proof, and the **validation target** ("repeat-
     purchase rate, not points issued").
  3. **Guardrail**, the risk envelope ("no retroactive backfill; points liability
     must reconcile with revenue").
  Requirement = "build X." Bet = "we believe X moves S; we'll know by M; we won't
  cross R." The Signal is exactly what e2e validates against.
- **Ask Mode (human-in-the-loop):** agent explores, can't write files, ends in a
  **Grilling Session**. **Implement Mode (AFK / "Night Shift"):** agent executes
  autonomously against the agreed plan.
- **On-slide script: the Grilling Session**, the agent interviews the *architect*
  about edge cases until it has a structured hypothesis; the result is logged to a
  **Bet Register**. (Also a wink: this very talk was built this way.) Mapped to a
  **Magento cart price rule (promotion)** feature:

  > **Architect:** "@agent, before any code, interview me about the edge cases of
  > a cart price rule for this Magento 2 store until you have a structured
  > hypothesis. Do not write files yet."
  > **Agent:** "Does it stack with coupon codes or is it exclusive? How does it
  > interact with rule priority and 'discard subsequent rules'? Which websites and
  > customer groups is it scoped to?"
  > **Architect:** "Exclusive , if a coupon applies, skip this rule. Respect
  > priority and stop on first match. All websites, logged-in customers only. The
  > signal is units per order, not discount dollars given. Log it to the Bet Register."
  > **Agent:** "What happens on a partial credit memo, does the discount recalculate?
  > And does the rule discount double-count against tax?"
  > **Architect:** "Discount recalculates proportionally on refunds; it must never
  > re-discount already-reduced items, and it reconciles in credit memos , that's a
  > success signal too."

- Validation evidence = e2e tests (MFTF / Playwright) against the Bet's success
  signals (e.g. *units per order lifts*, *rule stays exclusive with coupons*,
  *discounts reconcile in credit memos*).

### 3d-bis. Validate in a running system, preview environments (Upsun)

- **Validation needs a running system, not a mock.** Per Bet, spin up a real,
  ephemeral **Upsun preview environment**, the system actually runs.
- **Two checks run there:**
  1. **e2e** against the Bet's **Signal** (the validation target from 3d).
  2. An **evaluator agent** attempts to fulfill the Bet end-to-end and **judges the
     result**, kept **separate from the generator** that built it (planner /
     generator / evaluator; nothing grades its own work).
- This is the **earned, substantive Upsun role inside the V&V core** (distinct from
  the Stage-7/8 shared-infra slide). The preview env is where validation stops being
  opinion and becomes evidence.

### 3e. Close the loop, the factory learns
- Every V&V outcome, **pass or fail, feeds the next iteration's context**, the
  **ratchet** (each `AGENTS.md` line traceable to a specific thing that went wrong;
  successes become patterns). The flywheel is now complete and self-reinforcing.

**Slide ideas:** V/V two-box → three-layer reveal (progressive disclosure);
proof-artifact screenshots (`code`/`image`); Tipping Point chart (`stat`/chart);
four pillars (`cards`); Grilling Session script (`code`/`statement`); flywheel
completed with the feedback arrow highlighted.

## 4 · Where it's going, from your laptop to the factory (≈8 min)

**Beat:** what-could-be (the horizon, made credible).

- **Stage 6, Operating System:** agents are team members ("3 engineer slots, 5
  agent slots"). Context becomes **shared infrastructure**, a **Context Engine /
  social information fabric** that bottles expertise (historical PR comments, Slack
  decisions, the "battle scars") and resolves Doc Rot by treating the codebase as
  source of truth. TDD becomes a dependency (weak suites get gamed). **Eval becomes
  the product.** Token budgets + per-run observability.
- **Stage 7, Bright Factory:** agents write and ship; human steps back to
  supervisor. The human is the **Architect of Intent**, defining the **Risk
  Envelope** ("roll back if the canary shows a 2% latency increase"), not the sprint.
- **Stage 8, Autonomous Factory:** the loop goes **recursive**, agents monitor
  production signals and **generate their own Bets**, feeding the Bet Register.
  (Agor's role ladder coder→context-architect→conductor→hypervisor; supervisor
  agents, trigger chains, circuit breakers, policy systems.)
- **The infra reality (one explicit Upsun slide):** none of this works while agents
  loop on individual laptops. The autonomous factory needs **shared, ephemeral,
  sandboxed, observable infrastructure, cost per *workflow*, not per *seat*.**
  *This is the problem we work on at Upsun.* Framed as the category, then move on.
- Caveat: Agor framing is a vendor post, cite the model, don't present its phases
  as settled fact. Keep the skeptic's tone from Section 1.

**Slide ideas:** Stage 6-8 progression (`section` dividers + `cards`); Risk
Envelope as a `statement`; the recursive loop (flywheel with a "production
signals → new Bet" arc); single Upsun `statement`/`image` slide.

## 5 · Close, Relocate your judgment (≈3 min)

**Beat:** return (the lesson the audience applies).

- Recap the relocation: **Verification → machine. Validation → you. The Bet → your
  craft.**
- **DO THIS** (empowerment-framed, trimmed; drop the "NOT THAT / slop" fear list):
  - Quality control is *system eval*, move your eyes from tabs/spaces to alignment
    and intent.
  - Manage the **Risk Envelope**, define the signals and the jigs that constrain
    agents.
  - **Trust through evidence**, demand the SHA, demand the video.
- The vision: **one engineer, a fleet of agents, an impenetrable system of
  verification.** The Industrial Age of software is here, relocate your judgment
  to where it matters.
- **Final line:** *"Stop shipping code that looks right. Start architecting systems
  that prove it."*

**Slide ideas:** the three relocations (`cards` or `statement`); DO THIS
(`cards`); closing line as `closing` with CTA.

---

# Narrative checks (against global-resources/presentation-rules.md)

- **Sparkline:** oscillates what-is (pipeline, Islands, coordination debt) ↔
  what-could-be (the loop, the factory) throughout. ✔
- **Hero = the audience:** the developer is promoted to architect; we are the
  mentor handing them the tool (the harness). ✔
- **Signposted sections** with explicit time budget. ✔
- **One idea per slide / glanceable / no bullet walls:** enforced by the Dispatch
  layouts (statement, stat, cards, code). ✔
- **Failure story:** ✔ resolved, the agent that edited a failing test to make it
  pass (Section 3b), which is *why* the tamper-proof-tests rule exists (read-only +
  edit-detection + signed attestation). Ties the ratchet to a real scar.
- **Define axioms early:** Verification vs Validation defined before heavy use. ✔

# Open TODOs before @slides

- ✔ **Opening stat:** Terminal Bench 2.0, 30th → 5th, harness-only, same model
  (Section 0).
- ✔ **Failure anecdote:** agent edited a failing test to pass (Section 3b).
- ✔ **Grilling Session:** mapped to a Shopware loyalty-points feature (Section 3d).
- ✔ **Final one-liner:** *"Stop shipping code that looks right. Start architecting
  systems that prove it."*
- Still want a real **Tipping-Point** figure for the 3c chart (distinct from the
  opening stat), or present it qualitatively (Smart Zone / Dumb Zone) without a
  hard number.

# Q&A prep

- "Doesn't this just move the bottleneck to spec/Bet writing?"
- "How do you validate non-deterministic agent output without re-reading every diff?"
  (Answer: layer 2, e2e against written intent; layer 3 is the only human bit.)
- "Where does the human stay accountable?" (The Risk Envelope + the Bet.)
- "Isn't 'industrialization' just deskilling?" (The spine: programming was downstream;
  judgment is the craft. Everyone can ascend.)
- Upsun infra / cost-per-workflow specifics (if pushed).
