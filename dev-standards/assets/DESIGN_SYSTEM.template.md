# Design System — [CUSTOMIZE_HERE: Project Name]

The single source of truth for this project's visual language. All UI must follow it. When you add a new shared component or token, document it here so the system stays current.

> Stack: Next.js 15+ · Tailwind CSS v4 · shadcn/ui · Framer Motion · Lucide React
> Conventions: see the `dev-standards` skill. This file holds the project-specific tokens and component catalogue.

---

## 1. Design principles

[CUSTOMIZE_HERE: 3–5 short principles that define this product's feel, e.g. "Calm, content-first, generous whitespace" / "Dense and utilitarian" / "Playful and tactile". These guide every UI decision below.]

---

## 2. Color tokens

Define semantic tokens (not raw colors) and map them to Tailwind theme / CSS variables. Components reference the semantic names, never hex values.

| Token | Light | Dark | Use |
|-------|-------|------|-----|
| `background` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Page background |
| `foreground` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Primary text |
| `primary` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Primary actions / brand |
| `primary-foreground` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Text on primary |
| `secondary` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Secondary surfaces |
| `muted` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Subtle backgrounds |
| `muted-foreground` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Secondary text |
| `border` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Borders / dividers |
| `destructive` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Errors / delete |
| `success` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Confirmations |
| `warning` | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] | Cautions |

```css
/* app/globals.css — Tailwind v4 @theme */
@theme {
  --color-primary: [CUSTOMIZE_HERE];
  --color-background: [CUSTOMIZE_HERE];
  /* ...map every token above... */
}
```

Dark mode: [CUSTOMIZE_HERE: class strategy (`dark:`) or system preference]. Every token must have a defined dark value.

---

## 3. Typography

- **Font family:** [CUSTOMIZE_HERE: e.g. Inter (sans), JetBrains Mono (code)] — loaded via `next/font`.
- **Scale:**

| Role | Size / line-height | Weight |
|------|--------------------|--------|
| Display | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] |
| H1 | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] |
| H2 | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] |
| H3 | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] |
| Body | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] |
| Small / caption | [CUSTOMIZE_HERE] | [CUSTOMIZE_HERE] |

Use the scale via Tailwind utilities; don't set arbitrary font sizes inline.

---

## 4. Spacing, radius & elevation

- **Spacing scale:** stick to Tailwind's spacing scale (`p-2`, `gap-4`, ...). [CUSTOMIZE_HERE: note any project-specific rhythm, e.g. "section padding = `py-16`"].
- **Border radius:** [CUSTOMIZE_HERE: e.g. `--radius: 0.5rem`; cards `rounded-xl`, buttons `rounded-lg`].
- **Shadows / elevation:** [CUSTOMIZE_HERE: define the 2–3 elevation levels in use and when each applies].

---

## 5. Motion (Framer Motion)

- **Default transition:** [CUSTOMIZE_HERE: e.g. `duration: 0.2, ease: "easeOut"`].
- **Standard patterns:** [CUSTOMIZE_HERE: page enter, list stagger, modal in/out — reference shared variants].
- Keep motion subtle and purposeful; always respect `prefers-reduced-motion`.

---

## 6. Component catalogue

The shared building blocks. Always build from these; never re-implement bespoke versions. Add new shared components here as they're created.

| Component | Source | Notes / variants |
|-----------|--------|------------------|
| Button | shadcn/ui | [CUSTOMIZE_HERE: variants — primary, secondary, ghost, destructive] |
| Input | shadcn/ui | [CUSTOMIZE_HERE] |
| Card | shadcn/ui | [CUSTOMIZE_HERE] |
| Dialog / Modal | shadcn/ui | [CUSTOMIZE_HERE] |
| [CUSTOMIZE_HERE: project component] | `@/components/...` | [CUSTOMIZE_HERE] |

---

## 7. Interaction rules

- **Every clickable element shows `cursor-pointer`** — buttons, links, clickable cards, icon buttons. (Tailwind preflight resets native `<button>` to the default arrow, so this is explicit even on buttons.)
- **Focus states are visible** on every interactive element (keyboard accessibility — never remove focus rings without an equivalent replacement).
- **Hover/active feedback** on interactive elements: [CUSTOMIZE_HERE: standard hover treatment].
- **Disabled states:** [CUSTOMIZE_HERE: opacity + `cursor-not-allowed`, no pointer events].

---

## 8. Accessibility baseline

- Color contrast meets WCAG AA for text.
- All interactive elements are keyboard-reachable and have accessible labels.
- Images and icon-only buttons have `alt` / `aria-label`.
- [CUSTOMIZE_HERE: any project-specific a11y requirements].

---

## 9. Icons

- **Library:** Lucide React. Use Lucide icons consistently; don't mix icon sets.
- **Default size:** [CUSTOMIZE_HERE: e.g. `size={20}`]. Icon-only buttons must have an `aria-label`.
