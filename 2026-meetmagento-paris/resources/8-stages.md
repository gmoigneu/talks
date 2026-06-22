# **The 8 stages of AI engineering maturity: a framework for engineering teams**

A few months ago, Steve Yegge published his 8 levels of AI-assisted development, and it clicked the moment I read it, because I had lived that exact progression myself, moving from autocomplete to running agents one step at a time. Framed as an AI trust gradient, it finally gave the industry a vocabulary for something most of us were already going through without a name for it. If you haven’t read it, save it for later.

Yegge’s levels, though, focuses on the individual developer. And that’s the thing: when you’re leading an engineering team, you’re not managing one trust gradient, you’re managing a whole distribution of them. You’ve got someone running parallel agents all day sitting next to someone who still thinks of AI as a fancier autocomplete, and both of them are shipping code. This is why the 10x productivity boost everyone keeps talking about almost never shows up at the org level. The hard part is getting the whole organization to move together, without the fast movers creating chaos and the slow adopters quietly falling behind.

So we took the same principles and looked at them from another angle: not the individual developer Yegge describes, but the team and the organization the team lives in. Eight stages of maturity, from “nobody has decided anything” to “the factory runs itself”.

A quick word on vocabulary, because we lean on it throughout. When we say *team*, we mean a group of people working together toward the same outcome: engineers, yes, but also product, design, QA, whoever it takes to ship software. When we say *organization*, we mean the whole collection of those teams, plus the leadership, budgets, and governance sitting above them.

And here’s the part that makes this an SDLC story and not just a developer story: the new software development life cycle isn’t just about developers. It’s about the whole team. The old boundaries between product, design, and engineering are getting blurry. A product manager can now vibe-code a working prototype instead of writing a three-page spec nobody reads. A designer can ship real HTML and CSS, not just a design system and a Figma file to hand off. That shift is the whole point, and it’s why thinking in terms of individual developers stops being enough.

Let’s lay out the whole map before we walk through it.

| Stage | Name | You’ll hear | One-line summary | Cost model |
| ----- | ----- | ----- | ----- | ----- |
| 1 | The vacuum | “I’m not allowed to use Claude at work, so I pay for my own subscription.” | No AI strategy, whether through silence or empty permission. Developers form habits without guardrails. | Personal credit cards or free tiers |
| 2 | The drift | “Oh, you should talk to Jane, she’s built something wild with agents.” | One engineer 10x’d their output with agents, and the rest of the team hasn’t noticed. | Personal subscriptions, some expensed |
| 3 | The islands | “Can we just move Jane to our team?” | One team ships in days, another takes weeks. The gap is creating real friction. | Still personal subscriptions |
| 4 | The standardization bet | “No more personal accounts. Everyone’s on the approved tooling.” | AI becomes an engineering capability, not a perk. Tools, governance, and training are funded deliberately. | Centralized subscriptions. The company pays. |
| 5 | The workflow redesign | “If it’s not in the spec, the agent can’t build it.” | Specs before code. Review is about risk, not diffs. The process changed, not just the tools. | Subscriptions plus API for CI/CD |
| 6 | The operating system | “We’ve got three engineer slots and five agent slots this sprint.” | Agents are team members now. Practices are coordinated across teams. | Token budgets per team. API spend tracked. |
| 7 | The bright factory | “Three agents running. One went off the rails, I caught it.” | Agents write and ship code from local dev machines. Engineers launch, supervise, and course-correct. | Seat-based subscriptions can’t scale to shared infra. You need API commitments. |
| 8 | The autonomous factory | “The migration ran, tests passed, the PR is up. Nobody touched it.” | Agents run on shared infra, on triggers. The team designs the system, not the code. | API on shared infra. Cost per workflow, not per person. |

## **A few honest caveats**

No organization sits cleanly on a single stage. You’ll spot some teams at Stage 6 and another still firmly in Stage 1\. The number is a center of gravity, not a label you pin on everyone.

Also, you shouldn’t skip stages. Go straight for autonomous agents without the governance, testing, and shared context underneath, and you just become another canceled project. But there’s a subtler reason to go one stage at a time: each stage hurts in its own particular way, and that pain is the lesson. The friction between a fast team and a slow one is what pushes a company to standardize. The grind of reviewing agent output line by line is what convinces a team to redesign the workflow. Skip the pain and you lose the reason to move on: nothing makes the case for the next stage like the current one starting to hurt.

And stay skeptical the whole way. The hype around this is loud, the evidence much quieter, so treat every promise here, including ours, with care.

## **Stage 1: The vacuum**

Leadership hasn’t taken a real position; at most, it bought a batch of licenses and stopped there. Developers form habits without guardrails: pasting code into whatever chat window is open, no shared context files, no agent setup, no managed API keys. The organization pays for more than it gets. But this is a learning phase, and I think that’s fine: people are building intuition for what these models can and can’t do, where the context window gives out, and which tasks are worth handing over at all. That intuition is the real return right now. Don’t mistake silence for inaction. Your developers have already decided for themselves.

## **Stage 2: The drift**

Stage 1 was about what the organization hadn’t decided; Stage 2 is about what individuals have decided on their own. One engineer quietly has agents handling a big chunk of their output, running off a personal stash of prompts, custom skills, and a carefully tuned AGENTS.md they keep on their own machine. The person beside them hasn’t changed anything in two years, and nobody flags it because individual variation has always looked normal. This is the last stage where inaction is free. Once the drift becomes visible, and it will, it turns into a team-level problem.

## **Stage 3: The islands**

The gap that used to run between individuals now runs between whole teams, and it shows up on the delivery calendar where everyone can see it: one team has committed shared AGENTS.md files to its repos, wired up a few MCP servers, and built a library of reusable skills and slash commands, and its throughput jumps, while the team next door still writes code like it’s two years ago. And it’s more corrosive than a speed difference, because it turns into a people problem. The fast team gets impatient waiting on the slow one for shared work; the slow team feels shown up and left behind. What started as a tooling gap hardens into resentment between teams, and that’s much harder to repair.

## **Stage 4: The standardization bet**

The first stage that needs real commitment from leadership: AI becomes a capability you build deliberately. Three things matter here. Context engineering becomes explicit work, with shared AGENTS.md files and a curated skill and prompt library in the repos, so the team encodes its knowledge once instead of every developer teaching the AI the same lessons. Security and governance come before scale: SSO and SCIM, secret scanning, PR gates that run on agent output, audit logs, and an approved list of models and tools behind a gateway, built before people run at full speed. And training is ongoing, not a one-off workshop, usually built around the champions from Stage 2\.

## **Stage 5: The workflow redesign**

Stage 4 upgrades the tools; Stage 5 redesigns the factory floor, changing how the work actually gets done. Spec-first becomes the default: the spec lives in the repo as the agent’s entry point, and an agent can’t work from a vague ticket any better than a junior developer can. Code review shifts from line-by-line to risk-based questions: does this match the spec? Do the tests prove it? What’s the blast radius if it’s wrong? CI gates treat agent-opened PRs exactly like human ones, and evals start running right next to the unit tests. Expect a productivity dip while the role moves from writing code to reviewing and orchestrating; that’s normal. Watch quality, not just velocity: more code shipped at lower quality isn’t speed, it’s incidents arriving sooner.

## **Stage 6: The operating system**

Stage 5 changed how a team works; Stage 6 changes what a team is made of and how teams coordinate. A sprint might hold three engineers and five agent slots, and the engineer now looks more like a product manager than a programmer: writing specs, arguing with the AI about them, checking the tests. TDD becomes a dependency, not a nice-to-have: agents optimize for passing tests, so a weak suite gets gamed and you won’t find out until production does. Parallel agents running in isolated sandboxes can burn more compute in a single sprint than a quarter of hosting, so token budgets and per-run observability stop being optional. And shared context becomes real infrastructure (project memory, skills, prompt libraries, MCP servers), maintained as team assets and coordinated across teams.

## **Stage 7: The bright factory**

The line from Stage 6 is who holds the pen. The agents now write and ship whole units of work with barely any human authorship, and the human steps back from driver to supervisor. Manufacturing calls the fully autonomous plants that run with no one inside dark factories; software isn’t there yet, the lights are still on. Most teams are still babysitting: agents kicked off from a terminal on someone’s laptop, looping locally and opening PRs from a dev machine, with no shared runtime and no central record of what ran or why. That local-machine detail is the one thing separating this stage from the next.

## **Stage 8: The autonomous factory**

The difference from Stage 7 is the difference between a self-driving car with hands hovering over the wheel and one where the passengers are reading a book: the technology can be identical but the trust level is not. Agents move off laptops and onto shared infrastructure: scheduled or event-triggered runs in ephemeral, sandboxed environments, with centralized logs and traces, so a migration that used to need babysitting runs overnight and reports its results in the morning. Recurring jobs become first-class (dependency updates, security patches, test expansion) with defined success criteria and automatic escalation when something fails. And eval becomes the product: the knowledge that lived in people’s heads now lives in agent configs, skills, and eval suites that gate every merge, encoded once and enforced automatically. That’s what makes autonomy safe rather than reckless: your standards no longer live in someone’s head, they live in the system.

## **Conclusion**

The question facing every engineering organization isn’t whether to adopt AI; most teams already have. The real question is whether the system underneath is good enough to be worth amplifying.

Because that’s what AI is, and I’m convinced of this: an amplifier. It accelerates what’s already there, the good practices and the bad ones alike. The organizations we’ve watched gain velocity without losing quality all share the same foundation: clear service ownership, comprehensive testing, documented services, automated standards. None of this is new. We’ve been preaching these best practices for years. AI just made their absence impossible to ignore.

The autonomous factory is where this is heading. Most organizations will spend the next two or three years getting there, and the hardest part won’t be the agents themselves: it’ll be trusting them enough to take them off individual laptops and run them on shared infrastructure. That trust isn’t a leap of faith. You build it the same way you always have, with evidence. One eval, one recurring task, one verified deployment at a time.
