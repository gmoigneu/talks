# Implementation plan — hands-on hardening of the deck

> Scope locked: **Recommended 7** (H1, H2, H3, H4, H5, H7, H9) · **build the
> full PHP/Shopware harness repo** · **apply all three accuracy fixes**.
> Audience is Shopware/PHP, so every code artifact is real PHP tooling pulled
> from `example-research.md` (verified), not illustrative TypeScript.
> **Nothing is edited yet — this is for review.**

---

## Part A — The harness repo (build first; it feeds the slides)

A real, runnable repo at **`resources/harness-demo/`**. It is both the
screenshot source for the code slides and the backbone of the H2 live demo.
Every config is a verified real tool from `example-research.md` Area 1.

```
resources/harness-demo/
├── README.md                       # what to screenshot, how to run the demo
├── composer.json                   # dev: phpstan, shopware/phpstan-shopware, qossmic/deptrac, phpro/grumphp, phpunit
├── AGENTS.md                       # H1: Judgment Boundaries + toolchain table (<60 lines)
├── CLAUDE.md                       # symlink → AGENTS.md  (the `ln -s` one-source-of-truth trick)
├── phpstan.neon                    # includes shopware/phpstan-shopware → NoEntityRepositoryInLoopRule active
├── deptrac.yaml                    # H9: Controller→Service→Repository ruleset ("no DB from the wrong layer")
├── grumphp.yml                     # H5: phplint · phpcs(ecs) · phpstan · phpunit as pre-commit gates
├── doc/adr/0001-no-db-in-templates.md   # Nygard ADR template (rule · why · enforced-by deptrac) — Bets-lineage fix
├── .claude/
│   ├── agents/critic.md            # H7: adversarial Critic Agent prompt
│   └── hooks/pre-tool-use.sh       # H5: git-push denial gate (illustrative; GrumPHP is the enforced gate)
├── src/
│   ├── Service/ActiveUsersFinder.php    # H2: the SILENT perf bug — findAll()->filter(), passes every gate
│   └── Controller/ReportController.php  # H9: a deliberate Deptrac violation (controller → repository) for the RED screenshot
├── tests/ActiveUsersFinderTest.php      # green on 100 rows
├── bin/bench.php                   # H2 demo: seed SQLite at N rows, time the finder → the 10k cliff
├── tests-e2e/loyalty-points.spec.ts     # one ATS/Playwright storefront test (data-testid selectors)
└── .github/workflows/ci.yml        # runs phpstan + deptrac + grumphp + playwright
```

**Two deliberately-distinct failure cases (so the slides don't contradict each other):**
- **H2 silent perf bug** — `ActiveUsersFinder` does `findAll()` then `array_filter()` in memory. It is **not** in a loop, so PHPStan's `NoEntityRepositoryInLoopRule` does **not** flag it; tests pass on 100 rows. *This is the case machines miss → only validation/human catches it.*
- **H9 caught case** — `ReportController` calls a repository directly (or a repo-call-in-loop). Deptrac (and `NoEntityRepositoryInLoopRule`) **do** flag it → red CI. *This is the class of problem you can encode once and never re-find.*

Keeping these separate is the whole point: H2 proves "tests aren't enough," H9 proves "so encode the rule you can." Both are screenshottable; `bench.php` makes H2 demoable live without booting Shopware.

**Screenshots to capture from the repo (for the slides):**
1. `AGENTS.md` Judgment Boundaries block (H1)
2. `deptrac.yaml` + a red `deptrac analyse` run on `ReportController` (H9)
3. `phpstan.neon` showing `shopware/phpstan-shopware` + a `NoEntityRepositoryInLoopRule` hit (H9)
4. `grumphp.yml` + a blocked commit, silent on pass / verbose on fail (H5)
5. `.claude/agents/critic.md` + a sample `NOT READY TO MERGE` verdict (H7)
6. `bench.php` output: 100 rows = 4ms, 10k rows = 1,900ms (H2)

---

## Part B — Slide changes (in deck order)

Legend: **[EDIT]** existing slide · **[NEW]** inserted slide · tag = H-item / fix.

| # | Slide (current) | Change | What it shows |
|---|---|---|---|
| 2 | Stat hook (Terminal-Bench) | **[EDIT]** notes only — *fix #2* | Correct attribution in notes: deepagents-cli, GPT-5.2-Codex, 52.8→66.5, vendor self-report, Feb 2026. On-stage stat stays clean "30th→5th, harness only." |
| 17 | Verification is not Validation | keep | (definition, unchanged) |
| 17b | — | **[NEW]** code · *H2* 🎬 | The silent perf bug PHP snippet + "green tests, still wrong." This is the **demo slide**. |
| 20 | The failure scar (edited test) | **[EDIT]** notes — *fix #1* | Back the scar with real citations: Anthropic 12%/65% sabotage (arXiv:2511.18397), ImpossibleBench "GPT-5 exploits 76%", EvilGenie test-edit detection. |
| 21 | The harness (4 cards) | **[EDIT]** — *fix #1, H5, H9* | Card 1 "Cryptographic proof SHA-256" → **"Tamper-proof tests"**: read-only/isolated tests + test-edit detection + signed result. Card 3 git hooks → name GrumPHP/CaptainHook. Card 4 architectural → name Deptrac + `NoEntityRepositoryInLoopRule`. |
| 21b | — | **[NEW]** code · *H9* | The real `deptrac.yaml` (Controller→Service→Repository) + red violation. "You don't keep finding N+1s — you prevent them." |
| 22 | Success silent / failures verbose | keep | (statement) |
| 22b | — | **[NEW]** code · *H5* | `grumphp.yml` pre-commit + a blocked commit. Enforcement in the environment, not the prompt. |
| 23 | PR carries its evidence | **[EDIT]** code — *fix #1* | Replace `output sha256: 9f2a1c…` with **in-toto test-result attestation (PASSED, DSSE-signed)** + `gh attestation verify ✓` + "tests read-only in CI". Validation half unchanged. |
| 26 | The Tipping Point (40–50%) | keep | (stat) |
| 26b | — | **[NEW]** stat · *H3* | "Deleted 95% of skills": 10k lines → 97%→77%; 553 gotchas → 68min→6min. + the assumption/evals/skills mental model. |
| 27 | Curate surgically (4 cards) | keep | (Persist/Select/Compress/Isolate) |
| 27b | — | **[NEW]** code · *H1* | The Judgment Boundaries block + the "can a tool enforce it?" decision rule + "every line earned by a failure." Cite AGENTS.md → Linux Foundation (AAIF, Dec 2025). |
| 29 | Schemas = the mold | **[EDIT]** small | Add one line: conformance is what Deptrac/PHPStan check for free (ties back to 21b). |
| 30 | Bets not requirements | **[EDIT]** credit — *fix #3* | On-slide/notes credit: Shape Up (Ryan Singer) — appetite + six-week circuit breaker. |
| 31 | Anatomy of a Bet | **[EDIT]** notes — *fix #3* | Note the Nygard ADR lineage; point to `doc/adr/0001` as the decision-record form. |
| 32 | The Grilling Session (dialogue) | keep | (dialogue) |
| 32b | — | **[NEW]** handout · *H4* | The verbatim `/grill-me` reusable prompt + the twist ("you don't even review the PRD — you already aligned"). |
| 34 | Preview env / two checks / evaluator | **[EDIT]** small | Name the real eval split: promptfoo `llm-rubric` (non-deterministic) + Behat/Gherkin (spec) as "nothing grades its own work." |
| 34b | — | **[NEW]** code · *H7* | `.claude/agents/critic.md` + a `NOT READY TO MERGE` verdict. Generator ≠ evaluator, fresh session. |

**Slide-count delta:** +8 new (17b, 21b, 22b, 26b, 27b, 32b, 34b, and the H1 decision-rule can fold into 27b). 44 → ~51–52.

**Pacing:** that's heavy for 45 min. To hold time I recommend **cutting/merging 3 thinner statement slides** so net ≈ +5. Candidates: merge 8+9 (Islands symptom + trap → one), 38 (eval-as-product → fold into 37 notes), 42 (relocations recap → it duplicates 43's mandate). I'll propose exact cuts in the diff; you veto any.

---

## Part C — The three accuracy fixes (exact before/after for review)

### Fix #1 — SHA-256 of test output → defensible reframe  *(touches slides 20, 21, 23)*
`example-research` is firm: "SHA-256 of the test OUTPUT" has **no established
named precedent**. The underlying threat is very real and citable; the *defense*
needs renaming.

- **Slide 23 code, before:** `- output sha256: 9f2a1c… (attached, not the test file)`
- **Slide 23 code, after:**
  ```
  ### Verification  (signed, not self-reported)
  - tests: 142 passed, 0 failed   ·   tests are read-only in CI
  - in-toto test-result attestation: PASSED  (DSSE-signed; subject digest a1b2c3…)
  - gh attestation verify ✓
  ```
- **Slide 21 card 1, before:** "Cryptographic proof / SHA-256 — Hash the test *output*, not the file."
- **Slide 21 card 1, after:** "Tamper-proof tests — read-only & isolated in CI · test-file-edit detection · DSSE-signed test-result attestation."
- **Slide 20 notes:** add the three citations (Anthropic 12%/65%; ImpossibleBench 76%; EvilGenie edit-detection).

### Fix #2 — Opening stat attribution  *(slide 2, notes only)*
- **Before (notes):** secondhand model confusion ("Claude Opus 4.6" vs "GPT-5.2-Codex").
- **After (notes):** "LangChain deepagents-cli, **52.8 → 66.5** on Terminal-Bench 2.0, **model fixed at GPT-5.2-Codex**, harness-only — Trivedy, Feb 17 2026. Vendor self-report on a fast-moving leaderboard; on stage say only 'Top 30 → Top 5, harness only.'" On-slide text unchanged.

### Fix #3 — Anchor Bets to Shape Up + ADRs  *(slides 30, 31)*
- Add a small credit line on slide 30: "lineage: Shape Up (Singer) + ADRs (Nygard)."
- Slide 31 notes point to the repo's `doc/adr/0001-no-db-in-templates.md` as the concrete decision-record form (Title / Status / Context / Decision / Consequences).

---

## Part D — Honesty flags carried into speaker notes
- Agor ladder / "factory" framings = vendor posts → cite the model, not settled fact (already in deck; keep).
- `graphify` token-reduction figures and any leaderboard ranking = self-reported / fast-moving → attribute precisely (slide 28, slide 2 notes).
- One new platform-awareness beat (optional, notes only): acknowledge **Shopware's own AI** (AI Copilot; Agentic Commerce sales channel, 6.7.10.0, May 2026) so the talk reads as platform-aware. Recommend a single sentence in the Stage-6/7 notes.

---

## Part E — Sequencing, deliverables, risks

**Order of work**
1. Build `resources/harness-demo/` (Part A) — all configs + the two failure cases + `bench.php`.
2. Verify it runs: `composer install`, `vendor/bin/phpstan`, `vendor/bin/deptrac analyse` (red on ReportController), `vendor/bin/grumphp run`, `php bin/bench.php`. Capture the 6 screenshots.
3. Apply the three accuracy fixes (Part C) — smallest, highest-correctness-risk, do while fresh.
4. Add/edit slides (Part B) using the real artifacts/screenshots.
5. Propose the 3 compensating cuts; you approve.
6. Re-check the deck renders (transition already `none`); slide numbers in `data-bar` notes still coherent.

**Deliverables**
- `resources/harness-demo/` (runnable).
- Updated `index.html` (~51–52 → ~48–49 slides after cuts).
- Updated `content.md` (reflect the new slides, the SHA-256 reframe, the demo decision reversal for H2, the Shape-Up/ADR lineage).
- A short `resources/harness-demo/README.md` doubling as the talk's "do this Monday" handout.

**Risks / things to confirm during review**
- **Demo reversal:** `content.md` locked "no live demo." H2 reverses that for one ~2-min beat (`bench.php`). Confirm you want the live `bench.php` run vs a recorded clip / static slide.
- **Slide-count growth** vs 45 min — confirm you're OK with the 3 proposed cuts.
- **Verify-vs-validate consistency:** H2 (uncaught) and H9 (caught) must stay clearly distinct on adjacent slides; I'll word them so they reinforce, not contradict.
- **Repo depth:** harness-demo is illustrative, not a full Shopware bundle — `phpstan-shopware` rules run against representative `src/` classes, not a booted Shopware kernel. Confirm that's acceptable (full bundle = much larger build).
- Versions/leaderboard move; re-pull the morning of the talk (slide 2, slide 28).
```

