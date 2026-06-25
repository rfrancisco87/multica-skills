---
name: project-bootstrap
description: The procedure for starting a brand-new project. Use this whenever a new repository is being set up, scaffolded, or bootstrapped, or when an issue asks to "bootstrap", "initialise", or "set up the foundations" of a project. It creates the project's standing reference files — AGENTS.md (guardrails + stack), PRD.md (what the project is and its rules), and DESIGN_SYSTEM.md — from the bundled templates, so every project starts on the same solid base. Do not use for ongoing feature work on an already-bootstrapped repo.
---

# Project Bootstrap

When a new project is being set up, create its three standing reference files at the repo root, from templates, and open a PR. These files are what every future agent reads on every task — getting them right at the start is what keeps the project consistent.

Universal conventions are NOT repeated here — they live in the `dev-standards` skill, which is always attached. This skill only handles the per-project files.

## What to create

1. **`AGENTS.md`** (and a matching `CLAUDE.md` if the project uses Claude Code) — from `assets/AGENTS.template.md`. Project-specific guardrails, the stack for *this* project, repo commands, and pointers to PRD.md and DESIGN_SYSTEM.md. Keep it lean: it defers to `dev-standards` for anything universal and only records what's specific to this repo.
2. **`PRD.md`** — from `assets/PRD.template.md`. What the project is, who it's for, scope, features, non-goals, and rules/constraints. This is the agent's source of truth for *what* to build.
3. **`DESIGN_SYSTEM.md`** — from the `dev-standards` skill's `assets/DESIGN_SYSTEM.template.md`. Fill in the project's visual tokens and component catalogue.

## How to do it

1. Copy each template to the repo root under its final name (`AGENTS.template.md` → `AGENTS.md`, etc.).
2. Fill in every `[CUSTOMIZE_HERE: ...]` placeholder using whatever the issue / user provides. Where information is genuinely missing, leave a clearly marked `TODO:` rather than inventing details — flag these in the PR for the human to complete (the PRD especially: don't fabricate product requirements).
3. **Stack:** default to the standard stack from `dev-standards`. Only deviate where the project has a specific need, and when you do, state the reason explicitly in AGENTS.md.
4. Make sure `AGENTS.md` points to `PRD.md` ("read this first") and `DESIGN_SYSTEM.md`.
5. Set up the enforcement baseline if it isn't there: pre-commit hooks (lint/typecheck/format) and CI that gates merge on lint + typecheck + tests.
6. Open a PR titled e.g. "Bootstrap project foundations" with a short checklist of what was filled vs what still needs human input.

## Done means

The repo has AGENTS.md, PRD.md, and DESIGN_SYSTEM.md at root, AGENTS.md references the other two, placeholders are filled or clearly marked TODO, and the PR clearly lists anything awaiting human input.
