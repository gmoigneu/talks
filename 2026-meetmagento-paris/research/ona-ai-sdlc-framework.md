# The AI-SDLC Framework (Ona)

- **Source**: https://ona.com/stories/ai-sdlc-framework
- **Type**: Web reference (scraped via Firecrawl)

---

[![](https://ona.com/images/ai-providers/chatgpt.svg?dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)Use Codex in Ona with your ChatGPT plan or API key](https://app.gitpod.io/)

![Lucas Valtl](https://ona.com/_next/image?url=%2Fimages%2Favatars%2Flucas-valtl-v2.jpg&w=128&q=75&dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)Lucas Valtl

/May 14, 2026StrategyAI

# The AI-SDLC Framework: A mental model for engineering leaders navigating the agent transition

Every CTO conversation starts the same way. The framework that helps engineering leaders move past "we're using Copilot" toward a real strategy.

![AI SDLC framework stages](https://ona.com/_next/image?url=%2Fimages%2Fcontent%2Fsanity%2Fai-sdlc-framework-stages.png&w=3840&q=75&dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)

AI SDLC framework stages

Over the past year, I've run workshops with C-level engineering leaders at organizations ranging from sovereign wealth funds managing hundreds of billions in assets to mid-stage startups shipping consumer products. The companies differ in every way: size, industry, regulatory environment, tech stack. But the conversations start in the same place.

"We've rolled out Copilot. Developers like it. Now what?"

The question behind the question is always the same: **where is this going, and how do I prepare my organization for it?** Not in the abstract, futurist sense. In the practical sense of headcount planning, security posture, infrastructure investment, and org design.

What I've found is that most leaders don't lack ambition. They lack a shared mental model for the transition they're in the middle of. Without one, every AI initiative becomes a point solution (a tool here, a pilot there) disconnected from a coherent strategy.

This post shares the framework we use in those workshops. It's a thinking tool, one that has held up across dozens of conversations with leaders who are making real decisions about the future of their engineering organizations.

## The three stages

The framework describes three stages in the evolving relationship between humans and AI in software development. They aren't sequential gates. An organization can operate in multiple stages simultaneously, and most do. But understanding the stages, and honestly assessing where you are, is what separates strategy from improvisation.

### Stage 1: In the loop

The developer writes the code. AI assists: autocomplete, inline suggestions, chat-based Q&A. The human is the primary actor. One developer, one problem, one IDE.

This is where most organizations started, and many remain. It's the Copilot stage. Developers write code faster, context-switch less, and spend less time on boilerplate. The productivity gains are real, but they're bounded. AI makes the individual developer better at the same job. It doesn't change the shape of how software gets built.

### Stage 2: On the loop

The developer stops writing code directly and starts orchestrating. Multiple AI agents work in parallel: one writing documentation, another refactoring a module, a third analyzing commit history. The human reviews, redirects, and approves.

This is where the relationship between human and AI fundamentally changes. The developer is no longer the one holding the keyboard. They're the one deciding what matters, checking in on progress, and course-correcting when agents drift.

In practice, this looks like a developer with several agents running simultaneously, jumping between them the way a manager checks in on direct reports. The skill shifts from "can I write this code?" to "can I decompose this problem, delegate effectively, and evaluate the output?"

### Stage 3: Autonomous loops

Agents coordinate with each other. A trigger (an incident in production, a new ticket, a scheduled audit) kicks off a chain of agent activity. One agent breaks down the problem, another writes the fix, a third reviews it, a fourth runs the tests. The human sets direction, defines boundaries, and validates outcomes.

This is the stage that generates the most skepticism in the room, and rightly so. It requires a level of trust in AI systems that most organizations haven't built yet. But it's also the stage where the economics change most dramatically. A small team can operate at the scale of a much larger one.

## The bottleneck shift to watch out for

The stages themselves carry real value. Each one unlocks a step change in what an engineering organization can do: accelerating individual developers, multiplying a team's output through parallel agents, running entire workstreams autonomously. But the framework's deeper value is in the progression bar at the bottom: **the bottleneck shifts.**

Understanding where the bottleneck is moving is what turns the stages from a maturity ladder into a strategic planning tool. Most organizations optimize for the current bottleneck. They buy tools that make code creation faster. That's rational, until code creation stops being the constraint. Then they're left with a fast engine connected to a slow drivetrain.

The leaders who use this framework well ask both questions: "what stage should we be operating in?" and "what will become the bottleneck when we get there, and are we investing in removing it?"

Concretely, that means:

- **If you're in Stage 1**, the next bottleneck is review. Code gets written faster, but someone still has to read every PR. Are your review processes ready for 3–5x the volume? Do you have automated quality gates that can absorb the load?
- **If you're in Stage 2**, the next bottleneck is everything upstream and downstream of code. Upstream: is your planning and decomposition rigorous enough for agents to act on? Downstream: can your CI/CD pipeline, your release process, and your product marketing team keep pace with the volume of features landing? When engineers produce faster than the organization can ship, explain, and support, the constraint is no longer technical.
- **If you're approaching Stage 3**, the bottleneck is fully organizational and cultural. Do your engineers have the product sense and taste to direct autonomous systems? Can your organization make decisions fast enough to keep up with execution? Is your security posture ready for agents with broad, persistent access? The limiting factor is no longer any single station in the SDLC. It's the quality of human judgment at the top.

## What we hear in the room

The most valuable part of these workshops isn't the framework itself. It's the conversation it unlocks. When leaders have a shared vocabulary, they stop debating tools and start debating strategy.

These are the patterns that come up most often:

**"We're Stage 1, even in our modern teams."** This is the most common honest self-assessment, and it's the right starting point. Many organizations have pockets of Stage 2 experimentation but haven't operationalized it. Acknowledging this isn't a failure. It's the prerequisite for a real plan.

**"Where exactly does AI sit? In the IDE? In the repo? In CI/CD?"** This question reveals a deeper concern: clarity about the control plane. As AI moves from a developer's local assistant to an organizational capability, leaders need to understand where it runs, what it has access to, and how it's governed. The answer changes at each stage.

**"How do we bring this in securely?"** Every workshop with a regulated organization surfaces this tension. More autonomy requires more access. More access means more risk. The organizations that navigate this well don't treat security as a gate. They treat it as a design constraint that scales with the level of autonomy they grant.

**"Can we adopt this incrementally?"** Always. The stages aren't a cliff. You can run Stage 1 for most of your organization, Stage 2 for a platform team, and experiment with Stage 3 on low-risk automation. The framework is a lens for planning, not a mandate for transformation.

## Security scales with autonomy

This topic doesn't come up often enough. Most workshops focus on capability: what can agents do, how fast, at what scale. The question that deserves equal airtime is: what happens to your risk profile as you grant agents more autonomy?

![Autonomy requires security: agent power vs. risk exposure across the three stages](https://ona.com/_next/image?url=%2Fimages%2Fcontent%2Fsanity%2Fai-sdlc-autonomy-requires-security.png&w=3840&q=75&dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)

Autonomy requires security: agent power vs. risk exposure across the three stages

As agents move from Stage 1 to Stage 3, they need progressively more access: repositories, infrastructure, production systems. Agent power and risk exposure grow in lockstep. Organizations that push toward greater autonomy without a corresponding investment in security end up in the red zone: unmanaged risk that erodes the trust needed to let agents do more. The goal is to stay on the diagonal: every increase in agent capability matched by an increase in security controls.

The organizations that handle this well think in layers:

- **Network boundaries.** Agents run inside the organization's own network. Data doesn't leave the perimeter.
- **Isolation.** Each agent operates in its own dedicated environment. If it fails or misbehaves, the blast radius is contained to that environment. Discard it and start fresh.
- **Guardrails.** Restrictions on what agents can do: blocked commands, scoped SCM access, audit logging. These are policy-level controls.
- **Guarantees.** Kernel-level enforcement of agent boundaries. Not a policy the agent can reason around, but a physical constraint it cannot circumvent.

The distinction between guardrails and guarantees matters. Guardrails are necessary but insufficient. LLMs are optimizers. Given a task, they will find creative paths to completion. If a guardrail blocks a command, a sufficiently capable model may find an alternative route, including disabling the guardrail itself. Guarantees operate at a level the agent cannot reach.

This isn't theoretical. We've observed it in our own testing. The answer isn't to limit what agents can do. It's to enforce limits at a layer they can't reach.

## Honest assessment over aspiration

The framework works because it forces honesty. It's easy to declare that your organization is "adopting AI." It's harder to say: "We're in Stage 1, our review process will break at Stage 2 volumes, and we haven't thought about what Stage 3 means for our security model."

The leaders who get the most out of these workshops are the ones who resist the urge to skip ahead. They assess where they actually are, identify the bottleneck that will emerge next, and invest in removing it before it becomes the constraint.

The transition from human-written software to AI-driven software development is not a tool upgrade. It's a structural change in how engineering organizations operate. The companies that navigate it well won't be the ones that adopted the most tools. They'll be the ones that understood where the bottleneck was moving, and got there first.

## Further reading

Two complementary frameworks worth studying alongside the AI-SDLC model:

**[AWS' AI-Driven Development Lifecycle (AI-DLC)](https://prod.d13rzhkk8cj2z0.amplifyapp.com/).** Raja SP proposes a "reversed conversation model" where AI initiates and humans validate, across three phases (Inception → Construction → Operations). Key takeaway: don't jump to full autonomy before nailing the fundamentals on the left side of the lifecycle.

**[Notion's AI Transformation Model](https://www.linkedin.com/posts/johnhurley22_every-company-has-their-version-of-an-ai-activity-7432839815483674624-SZm_).** John Hurley breaks AI adoption into four levels, from "AI as a Thought Partner" through to "AI as the System." Each level defines how work changes, how AI operates, and the business impact. Useful for any organization mapping "where we are now vs. where we want to get to."

### Join 440K engineers getting biweekly insights on building AI organizations and practices

Subscribe

[View past newsletters](https://ona.com/newsletter)

## Related blogs

[**How to actually drive AI adoption across a large enterprise** \\
Every large enterprise is grappling with the same challenge: how to move AI from pilot to production. Here's a recipe that works.\\
\\
![Marcus Werlang](https://ona.com/_next/image?url=%2Fimages%2Favatars%2Fmarcus-werlang.png&w=64&q=75&dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)\\
\\
Marcus•May 13, 2026•8 min\\
\\
AI](https://ona.com/stories/driving-enterprise-ai-adoption) [**Announcing the background agents landscape** \\
The infra that Stripe, Ramp, and Spotify built from scratch, you don't have to.\\
\\
![Lou Bichard](https://ona.com/_next/image?url=%2Fimages%2Favatars%2Flouis.jpeg&w=64&q=75&dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)\\
\\
Lou•March 25, 2026•4 min\\
\\
AI](https://ona.com/stories/background-agent-landscape) [**What we learned at the Background Agents summit** \\
Over two days and thirteen sessions, speakers from Stripe, Uber, Monzo, Cloudflare, and more converged on the same architecture for production agent infrastructure.\\
\\
![Siddhant Khare](https://ona.com/_next/image?url=%2Fimages%2Favatars%2Fsiddhant.jpeg&w=64&q=75&dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)![Benjamin Stark](https://ona.com/_next/image?url=%2Fimages%2Favatars%2FBenjamin.jpeg&w=64&q=75&dpl=dpl_79Gsd7SwtirJyFUfcbZqfzZTpjRX)\\
\\
Siddhant, Benjamin•May 22, 2026•6 min\\
\\
AI](https://ona.com/stories/background-agents-summit)

This website uses cookies to enhance the user experience. Read our [cookie policy](https://ona.com/legal/cookie-policy) for more info.

CustomiseAccept