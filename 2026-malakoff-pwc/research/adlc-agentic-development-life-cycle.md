# ADLC — Agentic Development Life Cycle

- **Source**: https://www.adlc.io/#phases
- **Type**: Web reference (scraped via Firecrawl)

---

ADLC / Agentic Development Life Cycle

# The SDLC was designed for a world where humans were the primary execution unit.  That world is over.

ADLC is a new operating model for software delivery — built for a world where agents
execute, humans govern, and the pipeline becomes a loop.

[Read the Manifesto](https://www.adlc.io/#manifesto) [Explore the Phases](https://www.adlc.io/#phases)

// THE MANIFESTO

ADLC is not SDLC with AI tools added. It is a different operating model — redesigned for a world where the
primary execution unit is an agent, not a human.


Not This

### SDLC with AI tools added

Adding Copilot to your workflow isn't ADLC. Bolting an AI test tool onto QA isn't ADLC. These are
productivity improvements inside an unchanged operating model. Valuable. Not transformative.

Not This

### Removing humans from delivery

The opposite is true. ADLC requires more deliberate human involvement — at higher-order decisions, at
governance points, at the boundaries where agent output meets business intent. Human judgment doesn't
disappear. It relocates.

Not This

### A methodology or framework

ADLC doesn't prescribe standups, ceremonies, or ticket formats. It prescribes a different structure for how
work flows when agents are the primary execution unit. The unit of analysis is the delivery system, not the
sprint.

// FROM PIPELINE TO LOOP

THE SDLC PIPELINE

Requirements↓Design↓Develop↓Test↓Deploy↓Maintain

Sequential. Specialist-owned. Gate-controlled. Designed for humans.

THE ADLC LOOP

IntentGenerateValidateGovernDeployObserve

Concurrent. Agent-executed. Human-governed. Designed for loops.

The pipeline metaphor assumes sequential dependency. You cannot test what has not been developed. You cannot
deploy what has not been tested. This assumption was correct when humans were the execution unit.

Agents break this assumption completely. An agent generates code and tests simultaneously. Documentation is a
byproduct of generation, not a downstream task. The pipeline collapses into a loop.

// THE SIX PHASES

The phases of ADLC are not stages. Work does not move through them one at a time.
They are modes the delivery system operates in simultaneously, with different agents and humans active in each
mode at any given moment.

01

Phase 01

Intent

The hypothesis layer. Bets replace requirements.

In SDLC, planning produces requirements: a specification of what to build, written as if
the outcome were already known. In ADLC, planning produces bets — structured hypotheses about what to learn,
what to build, and what signal will resolve the question. The artifact is a Bet Register: a portfolio of
active hypotheses, each with a learning objective, a generation target, a resolution signal, and a decision
deadline.

Teams stop writing features and start writing questions. The measure of a good Intent
phase is a precise statement of what you do not yet know and how you will find out.

02

Phase 02

Generate

The creation layer. Agents execute; architects govern.

In ADLC, generation is parallel agent execution across the full artifact surface of a
feature. Code, tests, API documentation, database migrations, and deployment configurations are generated
together, not in series. The human role is not to write code — it is to provide precise intent context,
architect the boundaries within which generation occurs, and make decisions when generation surfaces
ambiguity.

Engineering effort shifts from writing to directing. The primary skill is the ability
to decompose Intent into precise generation contexts that agents can execute against without losing fidelity
to the original bet.

03

Phase 03

Validate

The continuous verification layer. Runs in parallel, not after.

In ADLC, validation is a continuous agent responsibility that runs alongside generation
from the moment a bet enters the delivery loop. Agents generate code and simultaneously generate test
coverage. Agents identify edge cases, flag regressions, and surface failure modes before a human reviews a
single line. The critical failure mode is Validation Debt: bets that have been prototyped but never validated
against real signal — invisible, accumulating, hiding behind the appearance of speed.

Quality is designed into generation, not inspected into releases. The measure of a
healthy Validate phase is bet resolution rate, not test coverage percentage.

04

Phase 04

Govern

The human judgment layer. The phase ADLC adds.

Govern is the phase ADLC adds to SDLC, not the one it replaces. It is about checking
alignment, not quality: does this output serve the intent? Does the signal support advancing this bet? These
questions require context that is not in the codebase — strategic tradeoffs, relationship risk, market timing,
organizational appetite for failure. They require accountability that agents cannot hold. Govern does not stop
the delivery loop. It redirects it.

Leadership's primary delivery responsibility shifts from approving features to
governing agent output against strategic intent. The cadence of Govern decisions — not the cadence of sprints
— determines delivery velocity.

05

Phase 05

Deploy

The release layer. Agent-orchestrated; human-approved.

Deployment orchestration is an agent responsibility. Feature flags, canary releases,
rollback triggers, and environment promotion are agent-managed processes operating within parameters humans
define. The human role is to set the risk envelope: what traffic percentage triggers a full rollout decision?
What signals trigger automatic rollback? Deploy in ADLC is fast and recoverable by design.

Deployment frequency increases dramatically; deployment anxiety decreases
proportionally. The mental model shifts from big-bang release to continuous calibration.

06

Phase 06

Observe

The signal layer. Closes the loop. Makes ADLC recursive.

Observe is not downstream from anything. It runs continuously alongside every other
phase and produces the signal that determines which bets resolve, which need iteration, and what new bets the
next Intent phase should contain. Agents monitor behavior, analyze usage, surface anomalies, and generate
hypotheses that feed back into the Bet Register. Humans govern the interpretation. Observe is the phase that
makes ADLC honest.

The distinction between product development and product operation collapses. The loop
never stops — it compresses, learns, and recalibrates continuously.

// FIVE PRINCIPLES

These are not guidelines. They are the structural commitments that distinguish
ADLC from SDLC with AI tools. An organization that cannot commit to all five is operating SDLC with acceleration
— not ADLC.

01

### Concurrency over sequencing

ADLC phases run in parallel. Generation and validation are simultaneous. Observation feeds intent
continuously. Any process that forces phases into strict sequence is imposing SDLC logic on an ADLC system.


02

### Governance over execution

Human value in ADLC is concentrated in judgment, not execution. Organizations that redeploy humans freed from
execution into more execution are wasting the transformation. The investment goes into governance capacity.


03

### Bets over requirements

Intent is hypothesis-driven. The measure of a good planning process is not the completeness of the
specification — it is the quality of the question. Teams that cannot articulate what they need to learn before
they build are not ready to operate ADLC.

04

### Loops over gates

Feedback is continuous in ADLC, not milestone-based. Gates stop the loop to inspect it. ADLC instruments the
loop to observe it in motion. The goal is not to catch problems at gates — it is to surface problems before
they become decisions.

05

### Signal over assumption

Observe is not optional. A delivery system that generates without observing is compounding its assumptions at
agent speed. Signal — from users, systems, and markets — is what separates a learning organization from a
fast-moving one.

// WHO ADLC IS FOR

### This is for you if...

- →AI agents in your delivery pipeline are generating production-quality
code faster than your review process can handle
- →Your primary delivery bottleneck has shifted from development speed to
governance quality and signal clarity
- →You understand that the competitive response to a structural change is
a structural change — not a faster pipeline
- →You are building toward a delivery model where agents execute and
humans govern

### This is not for you if...

- ✗You are looking for a 20% productivity improvement
- ✗You believe AI is a better autocomplete
- ✗You are not yet ready to redesign the delivery model itself

// ADLC OS

ADLC OS is the operating layer for teams running the Agentic Development Life Cycle. Tooling, observability,
and governance infrastructure that makes ADLC operational — not theoretical.

\[ STATUS: IN DEVELOPMENT \]

[Reach out on LinkedIn to join](https://www.linkedin.com/in/asafsaar/)