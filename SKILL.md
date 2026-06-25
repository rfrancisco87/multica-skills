---
name: dev-standards
description: The universal engineering conventions that apply to every project — default stack, golden rules, code style, data layer, testing, and the git/PR workflow. Always apply this skill on any coding, scaffolding, refactoring, review, or PR task, even when the user doesn't explicitly mention conventions, so that work stays consistent across all repositories. Project-specific architecture and domain rules live in the repo's own AGENTS.md / CLAUDE.md and PRD.md, which always override anything here on conflict.
---

# Dev Standards

This is the standing "how we work everywhere" layer. It is intentionally project-agnostic. Anything specific to *this* project (architecture, domain logic, gotchas, the spec) belongs in the repo's `AGENTS.md` / `CLAUDE.md` and `PRD.md`. **On any conflict, the repo files win.**

## Default stack

Unless the repo says otherwise, assume:

- **Framework:** Next.js 15+ (App Router)
- **Language:** TypeScript, strict mode
- **Styling:** Tailwind CSS v4 + shadcn/ui
- **Animation:** Framer Motion v11+
- **Icons:** Lucide React
- **Database:** Neon PostgreSQL **or** Supabase, depending on the project (with Prisma when an ORM is used). Pick per project; follow whichever the repo already uses.
- **Deployment:** Vercel (default target)
- **Package manager:** pnpm
- **Testing:** Vitest + React Testing Library

If a repo uses a different stack, follow the repo. Do not "upgrade" or swap a project's stack without an explicit instruction.

## Golden rules (never break)

1. **Never push directly to `main`.** Always work on a feature branch and open a PR.
2. **One issue → one focused PR.** Keep diffs small and reviewable.
3. **Never modify `.env` files.** Reference environment variables; never set or print secret values.
4. **Never commit secrets or API keys.** If you need a new var, add it to `.env.example` with a placeholder and document it in the PR.
5. **Never delete migration files.** Only create new migrations forward.
6. **Always run tests and the build before opening a PR.** A red pipeline is not "done."
7. **Write tests for new behavior.** No new feature lands without coverage.
8. **Ask, don't guess, on irreversible or destructive actions** (data deletion, schema drops, force-push). Report the blocker instead.

## Code standards

- **TypeScript strict — no `any`.** Prefer precise types; use `unknown` + narrowing when a type is genuinely open.
- **Named exports**, not default exports — except Next.js pages/layouts and React components, which follow the framework convention.
- **Import order:** external packages → internal aliases (`@/...`) → relative imports, separated by blank lines.
- **Async safety:** wrap async I/O in `try/catch`; never swallow errors silently — log or surface them.
- **Formatting/linting** are not optional. Run the repo's format and lint scripts before committing; do not hand-format.
- **Server vs client:** default to React Server Components; add `"use client"` only when a component needs state, effects, or browser APIs.
- **Server Actions / route handlers:** validate all input at the boundary (e.g. Zod). Never trust client-supplied data.

## Styling (Tailwind + shadcn/ui)

- Compose UI from shadcn/ui primitives; don't reinvent components that already exist in the project.
- Tailwind utilities over custom CSS. Reach for a stylesheet only for genuinely global concerns.
- Keep class lists readable; factor repeated patterns into components, not copy-paste.
- **Every clickable element must show a pointer cursor.** Anything interactive — buttons, links, cards with `onClick`, custom dropdown triggers, icon buttons — gets `cursor-pointer`. Tailwind's preflight resets `<button>` to the default arrow cursor, so this is required even on native buttons, not just `div`s. If it's clickable, it points.

## Design system & reusable UI

- **Every project must have a `DESIGN_SYSTEM.md` at the repo root**, and the UI must follow it. It defines the project's colors, typography, spacing, radii, shadows, and the catalogue of shared components. If a project doesn't have one yet, create it from `assets/DESIGN_SYSTEM.template.md` (bundled with this skill) and fill in the project's tokens; keep it current as the UI evolves.
- **Always build from reusable elements.** Before writing new markup, check whether a shared component already covers it; if so, use it. If a pattern appears more than once, extract it into a reusable component rather than duplicating.
- **No one-off, copy-pasted UI.** Buttons, inputs, cards, modals, and layout primitives come from the shared component layer (shadcn/ui + project components), not bespoke markup re-implemented per page.
- **Tokens, not magic values.** Pull colors, spacing, and typography from the design system (Tailwind theme / CSS variables), not hardcoded hex codes or pixel values scattered through components.
- New UI should read as part of the same system — consistent with what `DESIGN_SYSTEM.md` describes. When you add a genuinely new shared component, document it there.

## Data layer (Neon or Supabase)

- Choose Neon or Supabase per project, and stick with whatever the repo already uses — don't migrate between them without an explicit instruction.
- When using Prisma, all schema changes go through migrations — `prisma migrate` — never by editing the DB directly. With Supabase's own migration flow, use that project's migration tooling instead; the rule is the same: migrations forward, never ad-hoc edits.
- Treat connection strings and service keys as secrets (see Golden Rules). For Supabase specifically, never expose the service-role key client-side — only the anon key is safe in the browser.
- Keep queries in a data/service layer, not inline in components.

## Animation (Framer Motion)

- Use Framer Motion for transitions and micro-interactions; keep them subtle and purposeful.
- Respect `prefers-reduced-motion`.

## Testing

- Unit/component tests with Vitest + React Testing Library.
- Test behavior and user-visible outcomes, not implementation details.
- New feature or bug fix → a test that would have caught it.
- `pnpm test` (and `pnpm build`) must pass locally before the PR.

## Git & PR workflow

1. Branch off `main` with a descriptive name (`feat/...`, `fix/...`, `chore/...`).
2. Reference the issue ID in the branch name, PR title, or body so it auto-links and closes on merge.
3. Commit in logical units with clear messages.
4. Open the PR only after tests + build pass.
5. PR description: what changed, why, how it was verified, and any follow-ups.
6. Address review comments by updating the same branch — don't open a new PR for the same issue.

## Runtime enforcement

Documentation alone gets ignored; enforcement is what makes conventions stick. When scaffolding a new project, set up:

- **Pre-commit hooks** (lint, typecheck, format) so bad code can't be committed.
- **CI/CD** that runs lint, typecheck, and `pnpm test` on every PR and blocks merge on failure.
- **Vercel preview deployments** on each PR — use the preview URL to verify the change live (especially UI) before merging to `main`, which deploys to production.

If these aren't present in a repo you're working in, flag it — but don't silently skip the checks they would have run.
