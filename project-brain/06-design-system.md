# Design System

## Philosophy

Design reusable components.

Avoid one-off layouts.

Favor consistency.

## Components

Navigation

Hero

Program Cards

Impact Statistics

Story Cards

Testimonials

CTA Banner

Resource Cards

Footer

## Principles

Accessibility first

Responsive first

Performance first

---

## Design Tokens

Locked color, typography, and spacing system for the Magnified Voices
redesign. Derived from the Brand System, Creative Direction, and the
design research folder, and confirmed through direct visual review.

Framework-agnostic CSS custom properties (`tokens.css`) and a JSON
equivalent for design tooling (`tokens.json`) live alongside this file.
**Never hardcode a hex value, font name, spacing number, or radius in a
component — always reference a token.** This is a Development Rule, not
a style preference.

### Color

Two functional accents, each with a distinct job rather than decorative
variety:

| Token | Value | Role |
|---|---|---|
| `--color-warm-white` | `#FBF9F5` | Page background |
| `--color-sand-100` | `#F1EEE6` | Alternate section background |
| `--color-sand-300` | `#D8D3C6` | Dividers, hairline borders |
| `--color-ink-600` | `#6B6A63` | Secondary / supporting text |
| `--color-ink-900` | `#22221F` | Primary text, headlines |
| `--color-terracotta-100` | `#FBEAE0` | Soft fill, badges, hover backgrounds |
| `--color-terracotta-600` | `#C6603C` | Primary CTA fill — energy / action |
| `--color-terracotta-700` | `#A34D2E` | Primary CTA hover / active |
| `--color-on-terracotta` | `#FFF3EC` | Text/icons on terracotta fill |
| `--color-teal-100` | `#E4EDE9` | Soft fill — stat cards, quote blocks |
| `--color-teal-700` | `#2E5E56` | Eyebrow labels, stat emphasis — trust / proof |
| `--color-teal-900` | `#1D3D38` | Text on teal-100 fill |
| `--color-on-teal` | `#FFFFFF` | Text/icons on teal-700 fill |

**Rationale:** Terracotta carries CTAs and moments of energy — it directly
answers the Strategy's "weak calls to action" problem by being the only
warm, saturated color on the page. Teal is reserved for trust-signaling
moments (Impact Statistics, testimonials), giving the Design Decision
"impact before ask" its own visual identity. The warm off-white base
(instead of stark white/gray) supports "hopeful, inclusive,
community-focused" — cold neutrals read corporate, which works against
the mission.

Use the **semantic aliases** in components rather than raw palette values
where possible: `--color-bg`, `--color-text-primary`,
`--color-text-secondary`, `--color-accent-action`,
`--color-accent-action-hover`, `--color-accent-trust`, `--color-border`.

### Typography

| Role | Family | Notes |
|---|---|---|
| Display / Hero headlines | **Anton**, uppercase | ~44–52px, line-height 1.0–1.05, +1% letter-spacing. Hero headlines and major section titles only — short phrases, never long-form. |
| H2 / Section titles | **Anton**, uppercase | ~28–32px, same treatment as display, scaled down. |
| Eyebrow / labels | **Inter**, medium | 11–12px, uppercase, +6% letter-spacing, teal. |
| Body copy | **Inter**, regular | 16–17px, line-height 1.65. 8th-grade reading level. |
| Subhead / card titles | **Inter**, medium | 18–20px, mixed case. |
| Testimonial / community quotes | **Fraunces**, italic, medium | 16–17px, teal. Reserved exclusively for first-person community voices. |
| Buttons / CTAs | **Inter**, medium | Sentence case, not uppercase — keeps CTAs approachable while Anton stays the only uppercase moment on the page. |

**Rationale — hybrid system:** Anton gives the site its "amplified voice"
moment where it matters most (hero headlines), directly embodying the
organization's name — bold, condensed, impossible to ignore. Inter keeps
everything else calm, legible, and scannable, which matters most for
Resource Seekers and first-time visitors who need to act quickly. Fraunces
italic is a deliberate device: it gives community members' own words a
distinct typographic identity from the organization's institutional
voice — a small typographic echo of "Magnified Voices" itself.

**Guardrails:**
- Anton is uppercase-only, headline-only. Never body text, never
  lowercase, never more than one weight/size combination per screen.
- Anton needs generous whitespace around it to read as confident rather
  than aggressive — pair with the larger spacing tokens (`--space-6`,
  `--space-7`).
- Fraunces italic is quote-only — don't reach for it as a general
  "editorial" accent elsewhere; its value is that it's reserved.
- Uppercase is always applied via CSS `text-transform`, never typed in
  literal caps, so screen readers pronounce words normally.

Load only the weights in use:
```html
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Inter:wght@400;500&family=Fraunces:ital,wght@1,500&display=swap" rel="stylesheet">
```

### Spacing

Base-8 scale.

| Token | Value | Use |
|---|---|---|
| `--space-1` | 8px | Tight inline gaps |
| `--space-2` | 16px | Default inline/stack gap |
| `--space-3` | 24px | Card padding |
| `--space-4` | 32px | Component-level spacing |
| `--space-5` | 40px | Sub-section spacing |
| `--space-6` | 64px | Section internal padding |
| `--space-7` | 96px | Spacing between major homepage sections |

### Radius

| Token | Value | Use |
|---|---|---|
| `--radius-sm` | 8px | Buttons, inputs, small controls |
| `--radius-lg` | 12px | Cards, panels, images |
| `--radius-pill` | 999px | Pill badges/tags only |

Soft enough to feel warm and human, restrained enough to stay trustworthy —
not so round it reads playful or childish.

### Elevation & Motion

Elevation is minimal by design — the Creative Direction calls for "minimal
UI," and research notes favor subtle interaction feedback over decorative
shadows.

| Token | Value |
|---|---|
| `--shadow-hover` | `0 4px 12px rgba(34, 34, 31, 0.08)` |
| `--duration-fast` | 150ms |
| `--duration-base` | 250ms |
| `--ease-standard` | `cubic-bezier(0.4, 0, 0.2, 1)` |

### Layout

| Token | Value |
|---|---|
| `--container-max` | 1200px |
| `--breakpoint-sm` | 640px |
| `--breakpoint-md` | 1024px |
| `--breakpoint-lg` | 1280px |

### Files

- `tokens.css` — build source of truth (framework-agnostic CSS custom
  properties)
- `tokens.json` — same values structured for design tooling (Figma
  Tokens, Style Dictionary)

### Open item

Component Library and Development Rules are still empty elsewhere in the
Brain. This token system is built to best-practice standard per the
Brain's own instruction to propose thoughtful solutions where documents
are incomplete. Once a specific build framework is confirmed (React/
Tailwind, Webflow, etc.), add a framework-specific export (e.g.
`tailwind.config.js`) alongside these files.