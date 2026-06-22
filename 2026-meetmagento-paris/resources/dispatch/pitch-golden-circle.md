---
title: "Upsun Dispatch — Pitch"
status: draft
last_updated: 2026-04-13
owner: guillaume
tags: [kickoff, pitch, golden-circle]
---

# Upsun Dispatch — Pitch

---

## WHY

Every developer on your team got faster this year. Cursor, Claude Code, Copilot. They're writing code two, three times faster than before. But the organization isn't shipping faster. A lot of teams are actually shipping slower.

All that extra code still needs to be reviewed by the same people. Still needs to be tested, secured, deployed through the same processes. The bottleneck just moved. Review backlogs are piling up. Security scans get skipped because nobody has time. Standards drift across repos because every dev uses agents their own way. Release cadence? Unchanged.

That's today's pain. But something bigger is happening underneath.

Code is getting commoditized. A product manager can vibe-code a prototype now and walk into a meeting with something that runs. Engineers are doing product work because agents handle the implementation. The lines between roles are moving fast, and most teams have no idea how to reorganize around that.

The whole software development lifecycle is getting rewritten right now. Nobody has a real answer for what it should look like.

We think Upsun can be the one to define it. That's what this project is.

## HOW

Today's tools put agents on your laptop. We're putting them in the team's workflow.

Background agents. Not assistants sitting next to one developer. Agents as participants in structured workflows alongside human engineers. Each has a defined role. The workflow orchestrates both.

What does that actually look like? A PR opens on GitHub. A CVE scan agent runs. A code review agent runs at the same time. A human engineer looks at the findings and makes a call. An agent applies the approved fix. The platform spins up a preview environment on Upsun so the team can see the change running on a real stack. A human approves the merge. An agent deploys to production.

That's one workflow. You could build another that goes end to end. A PM writes a feature brief in Linear. An agent turns it into a technical spec and a UX flow. A designer reviews and adjusts the design. An agent implements it. A human engineer reviews the code. The platform spins up a preview environment so the PM and designer can see it running. Everyone signs off, and an agent deploys to production. Idea to live, with agents, engineers, designers, and PMs all in the same flow.

Agents and humans taking turns in a structured flow, with the platform handling the handoffs. That's what we're building.

Three things guide how we build it. We ship with opinionated defaults: predefined workflows for what every team needs. CVE scanning, code review, build validation. Start in minutes, customize when you're ready. It's a standalone product. Phase 1 works on its own, no Upsun Cloud dependency. GitHub, agent compute, workflow orchestration. And we plug into what's already there. GitHub first, then GitLab, Linear, and whatever tools your team runs.

That's Phase 1. Phase 2, we integrate fully with Upsun Cloud and Blackfire. Agents spin up managed databases, caches, and queues per workflow. Preview environments on every PR so agents test on real stacks. Data cloning so agents work on production-like data instantly. Blackfire profiling embedded directly in the workflow. That's when it becomes the full experience, and that's when the product becomes something nobody else can offer.

## WHAT

So what does the product actually look like?

Triggers: GitHub events, schedules, API calls, manual runs. A workflow builder with a visual canvas, chat scaffolding, and YAML. Branching, parallelism, conditions. Background agents that run defined tasks on every event. And human checkpoints woven into every flow. Review gates, approval steps, decision points.

GitHub-first. API-first. Provider-agnostic from day one. Bring your own tokens.

We're starting with teams of ten to twenty developers. SaaS companies, but also organizations we're already talking to at Upsun. Teams using AI coding tools every day, feeling that gap between individual speed and org velocity. The product is built to scale up from there, and we'll expand to larger organizations quickly.
