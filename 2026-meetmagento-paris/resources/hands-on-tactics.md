# Hands-on tactics — a ranked menu

> Purpose: fix *"too much theory, not enough hands-on."* Every item is a
> copy-pasteable artifact, mapped to the slide it strengthens. Pick by ID
> (H1, H2…); nothing is in the deck yet.
>
> **Decisions so far:** menu first (deck untouched) · **one ~2-min live demo
> allowed** — demo candidates marked 🎬, my pick is **H2**.

## Ranked menu (scan this, then read detail below)

| ID | Tactic | Maps to | Format | Effort | Impact |
|----|--------|---------|--------|--------|--------|
| **H1** | AGENTS.md "Judgment Boundaries" (NEVER/ASK/ALWAYS) + "can a tool enforce it?" rule | 27, 29 | code slide + handout | M | ★★★★★ |
| **H2** 🎬 | The silent performance bug (passes every gate, wrong anyway) | 17 / 19 | code slide / demo | S | ★★★★★ |
| **H3** | "Deleted 95% of skills" — 97%→77%, 68min→6min + eval mental model | 27 (new before it) | code slide + stat | S | ★★★★★ |
| **H4** | The `/grill-me` prompt, verbatim (make slide 32 reusable) | 32, 33 | handout | S | ★★★★ |
| **H5** 🎬 | Git-push denial-gate hook — "success silent, failures verbose," literal | 21, 22 | code slide | S | ★★★★ |
| **H6** 🎬 | Induce-failure → add one rule → re-run clean (the ratchet, live) | 20, 35 | demo | M | ★★★★ |
| **H7** | The Critic Agent prompt — generator ≠ evaluator, made real | 34 | code slide | S | ★★★★ |
| **H8** 🎬 | The `/awesome` eval A/B — does the context line change the output? | 25 / new | demo | M | ★★★★ |
| **H9** | Architectural import-lint — make N+1 *structurally impossible* | 21 | code slide | S | ★★★ |
| **H10** | Coding agent vs background agent — "in the loop → on the loop" | 12, 33 | code slide (table) | S | ★★★ |
| **H11** | Vertical slices / tracer bullets — how to cut a Bet into work | new ~31, 34 | code slide | S | ★★★ |
| **H12** | Context offloading = `free()` for memory; "clear, don't compact" | 26, 27 | code slide | S | ★★★ |
| **H13** | Ralph-loop completion promise — `<promise>DONE</promise>` + convergence | 35 | code slide | M | ★★★ |
| **H14** | Trigger taxonomy + circuit breakers (S4 made buildable) | 39, 40 | code slide | S | ★★ |
| **H15** | Cross-cutting one-liner statement slides | various | statement | S | ★★ |

Effort: S = drop-in artifact · M = needs a new/reworked slide.

---

## Detail

### H1 — AGENTS.md "Judgment Boundaries"  ★★★★★
The one artifact the audience builds Monday. Most AGENTS.md content is wasted —
agents follow rules a linter already enforces, inflating cost. The file should
own *only* judgment no tool can enforce.
```md
## Judgment Boundaries
**NEVER:** weaken a test/gate to get green · add deps without discussion · guess on ambiguous specs
**ASK:**   before DB migrations · before deleting files
**ALWAYS:** explain the plan before coding · say what you didn't verify
```
Decision rule (own slide):
```
linter can enforce it? → tool config    CI can enforce it? → the pipeline
hook can enforce it?   → the hook        none of the above? → AGENTS.md
```
Backing: *LLM-generated context files cut task success +20% cost* (Gloaguen 2026).
"A pilot's checklist, not a style guide" — keep <60 lines, **every line earned by
a past failure.** → slides 27 / 29.

### H2 — The silent performance bug 🎬 (my demo pick)  ★★★★★
Tests pass, types pass, lint passes, spec is met — still wrong. The most
persuasive proof in the corpus that machines can't *validate*.
```typescript
async function getActiveUsers() {
  const users = await db.users.findAll();           // loads the whole table
  return users.filter(u => u.status === 'active');  // filters in memory
}
// Works on 100 rows. Dies at 10k. Only a human reading against the
// architectural contract catches it.
```
As a demo: show the green test run, then the 10k-row latency. As a slide: the
code + a critic verdict callout. → slide 17 (Verification is not Validation).

### H3 — "Deleted 95% of skills"  ★★★★★
Turns abstract "poisoned context" (slide 27) into a number. 10k generated lines
dropped a task **97%→77%**; trimmed to 553 hand-written gotchas → eval time
**68min→6min**. The model knows how to code; it needs to know the landmines.
```
assumption: the agent is perfect
evals:      find where the assumption falls short
skills:     write context ONLY for the gaps
```
→ new slide before 27.

### H4 — The `/grill-me` prompt  ★★★★
Slide 32 shows the dialogue but never hands over the prompt.
> "Interview me relentlessly about every aspect of this plan until we reach a
> shared understanding. Walk down each branch of the decision tree resolving
> dependencies one by one. For each question provide your recommended answer.
> Ask the questions one at a time."

Twist worth a line: you don't even review the PRD it produces — you already
aligned. → slides 32 / 33.

### H5 — Git-push denial gate 🎬  ★★★★
Agents try to `git push` to skip review; a hook blocks it.
```bash
# .claude/hooks/pre-tool-use.sh
if [[ "$TOOL" == "Bash" && "$COMMAND" =~ "git push" ]]; then
  echo "Blocked: use 'submit-pr' which runs verification first."; exit 1
fi
```
Principle: enforcement moves from *prompt* (ignorable) to *environment* (cannot
be). → slides 21 / 22.

### H6 — Induce-failure → ratchet → re-run 🎬  ★★★★
The ratchet, live and visceral: make the agent do something dumb, add one
AGENTS.md line or hook, re-run, it never recurs. "It's not a model problem, it's
a configuration problem." → slides 20 (the scar) / 35 (close the loop).

### H7 — The Critic Agent prompt  ★★★★
Slide 34 says "an evaluator, separate from the builder." Give the drop-in:
```md
# .claude/agents/critic.md
You are a rigorous Critic Agent. Skeptical by design: reject code that violates
the Spec or Constitution even if it "works." Favor false positives.
Output "## Verdict: PASS" or "## Verdict: NOT READY TO MERGE" with, per
violation: Violated / Impact / Remediation.
```
Run in a *fresh* session (Pocock: build with Sonnet, review with Opus after
`/clear`). → slide 34.

### H8 — The `/awesome` eval A/B 🎬  ★★★★
Reproducible proof that a context line does work. Put in AGENTS.md: "every
endpoint must use the prefix `/awesome`." Prompt "add an endpoint to save a
user" → expect `/awesome/user`. Run again with the rule removed — no model ever
invents that prefix. LLM-as-judge scores it. → slide 25 or new.

### H9 — Architectural import-lint  ★★★
Slide 21 mentions "no DB from templates" abstractly. Show the rule + the
principle: **"You cannot keep finding N+1s. You prevent them entirely."** Lint
the import graph so templates and the e2e suite can't import DB-touching modules.
→ slide 21.

### H10 — Coding vs background agent  ★★★
Clearest single artifact for role inversion (slide 12) and the Night Shift (33).
```
            Coding agent        Background agent
runs        your laptop         cloud, triggered remotely
triggered   you, manually       events / schedules / Slack / API
scope       one task/repo       across repos / teams / full SDLC
your role   IN the loop         ON the loop
```

### H11 — Vertical slices / tracer bullets  ★★★
AI codes horizontally (all schema → all API → all UI) so no feedback till the
end. Force thin slices:
```
GOOD: "Award points for lesson completion, visible on the dashboard."  (end-to-end)
BAD:  "Create the gamification service."                               (horizontal)
```
Tag issues `AFK` / `human-in-loop`, `blocked by: [1,2]` → a DAG agents parallelize.
Maps onto the loyalty-points Bet already in the deck. → new slide near 31 / 34.

### H12 — Context offloading / clear-don't-compact  ★★★
At ~60–80% capacity, write raw output to disk, keep a pointer + summary. "Long
windows don't negate structured state, they delay rot." Pocock: **clear, don't
compact — be the guy from Memento, same clean state every time.** → slides 26/27.

### H13 — Ralph-loop completion promise  ★★★
Agent isn't done when *it* says so — only when external tooling confirms.
```
Stop hook re-injects prompt until: <promise>DONE</promise>
P(complete) = 1 − (1 − p_success)^n   (n up to ~50)
caps 20–50 · rotate context at 60–80% · Docker sandbox
```
→ slide 35.

### H14 — Triggers + circuit breakers  ★★
```
triggers: scheduled (dep updates) · event (PR/CVE/alert) · fleets · swarms
contain:  token budgets · concurrency caps · resource caps · circuit breakers
"If every run starts with a dev typing a prompt, you automated the work, not the workflow."
```
→ slides 39 / 40.

### H15 — Cross-cutting one-liners (statement slides)  ★★
- "Context is the fuel; the LLM is just the engine. Wrong fuel, no performance."
- "Agents don't replace humans; they industrialize execution."
- "Agents are a high-pass filter for process maturity — they amplify good
  practices and the chaos of bad ones."
- "My agent survives 50 context compacts. Yours forgets after 1. The difference
  is *where the rules live*."
- "Individual speed ≠ organizational velocity. That's the false summit." (S1/S2)

---

## Demo candidates (one ~2-min slot)
- **H2 silent perf bug** — *recommended.* Self-contained, no tooling risk, lands
  the centerpiece (Verify ≠ Validate). Green test → 10k-row latency reveal.
- **H8 `/awesome` A/B** — most "magical" (context changes output live) but needs
  a working agent + judge on stage; more setup, more failure surface.
- **H6 induce-failure → ratchet** — visceral but the live failure is the riskiest
  to stage reliably.

## Honesty flags (deck's "mentor, not marketer" rule)
- Agor 7-phase ladder & background-agent "factory" framings are vendor posts —
  cite the model, don't present phases as settled fact.
- Real enterprise proof points if you want name-drops: Stripe ("Minions," ~1,300
  PRs/wk), Spotify (1,500+ PRs), Shopify (River), OpenAI.
