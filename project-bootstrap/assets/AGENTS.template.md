# AGENTS.md — [CUSTOMIZE_HERE: Project Name]

Guardrails and standards for AI agents working in this repository.

> **Universal conventions** (stack defaults, golden rules, code style, git/PR workflow, testing) come from the `dev-standards` skill — they are NOT repeated here. This file records only what is specific to **this** project.
>
> **Read `PRD.md` first** — it defines what this project is and its rules.
> **UI follows `DESIGN_SYSTEM.md`.**

---

## What this project is

[CUSTOMIZE_HERE: one or two sentences. For full detail, the agent reads PRD.md.]

## Stack (this project)

Default to the standard stack from `dev-standards`. Record only deviations here, with the reason.

- [CUSTOMIZE_HERE: e.g. "Standard stack. Database: Supabase (chosen for built-in auth)." or "Standard stack, no changes."]

## Setup & commands

```bash
[CUSTOMIZE_HERE: install]          # e.g. pnpm install
[CUSTOMIZE_HERE: dev]              # e.g. pnpm dev
[CUSTOMIZE_HERE: test]             # e.g. pnpm test
[CUSTOMIZE_HERE: build]            # e.g. pnpm build
[CUSTOMIZE_HERE: db / migrations]  # e.g. pnpm prisma migrate dev
```

## Architecture notes

[CUSTOMIZE_HERE: key folders, important modules, data flow, anything an agent must understand before touching code. Keep it short — point to deeper docs rather than duplicating them.]

## Project-specific guardrails

Beyond the universal golden rules in `dev-standards`:

- [CUSTOMIZE_HERE: e.g. "Never touch the billing module without human review."]
- [CUSTOMIZE_HERE: e.g. "All API routes require auth middleware."]
- [CUSTOMIZE_HERE: domain rules, external services, rate limits, etc.]

## Scope control

- Do only what the assigned issue describes. Do not refactor or "improve" unrelated code into the same PR.
- If you discover adjacent work that should be done, note it in the PR or open a new issue — don't expand the diff.

## When blocked

- After [CUSTOMIZE_HERE: e.g. 2] failed attempts at the same problem, stop. Post a comment describing what you tried, the errors seen, and what you think the blocker is. Do not keep flailing or make destructive changes to "get past" it.

## Repositories

<!-- Managed by Multica — do not edit by hand. -->
