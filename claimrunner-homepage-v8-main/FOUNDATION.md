# ClaimRunner foundations

Source of truth for **tokens:** [`tokens.css`](tokens.css).  
Source of truth for **why those tokens exist:** this file.

Use this when designing in Figma, writing copy, or reviewing UI. Don’t invent mid sizes, one-off colors, or layout rules that contradict the principles below.

**Living surfaces:** `index.html` + `styles.css` (marketing homepage v8), `legal.html` (long-form), eligibility flows (separate UI; still inherit these foundations where possible). Previous homepage: `archive/v7.html`.

---

## 1. Product context (design constraints)

ClaimRunner helps **self-represented people** navigate small claims, starting in **King County, WA**. The site is marketing + education first: waitlist, eligibility check, trust.

| Constraint | Design implication |
|------------|--------------------|
| High anxiety, low trust | Calm surfaces, clear hierarchy, no dark-pattern urgency, honest “not a law firm” framing |
| Not legal advice | Copy and UI must never imply prediction, strategy, or guaranteed outcomes |
| Mixed literacy / stress | Short sections, plain language, one job per block, generous spacing |
| Mobile-heavy browsing | Touch targets, stacked layouts under 900px, type that still works at 16px body |
| Early-stage product | Hero = brand + one promise + CTAs; don’t fake a full product dashboard |

---

## 2. Core theorems (marketing, consumption, accessibility)

These are the standing rules. Token tables exist to implement them.

### Marketing & conversion

1. **Brand-first first viewport.** Logo / product name is a hero-level signal. A headline must not overpower the brand. Test: if you strip the nav and the first screen could belong to another product, branding is too weak.
2. **One composition, not a dashboard.** The first viewport is one scene (brand, one headline, one short support line, one CTA group, one dominant visual). No stats strips, schedule chips, or secondary promos in the hero.
3. **One job per section.** Each section has one purpose, one H2, usually one short lead. If two stories compete, split the section.
4. **Primary action is obvious.** Solid blue = default path (waitlist). Outline / quiet = secondary (eligibility, dismiss). Don’t ship two equal primary buttons.
5. **Trust before cleverness.** Self-serve legal-adjacent tools lose users to doubt faster than to boredom. Prefer clarity over novelty.
6. **Progressive disclosure.** FAQ uses `<details>`; legal is a dedicated page; modals for waitlist. Don’t dump every policy into the hero.

### Consumption & readability

7. **Measure beats canvas.** Marketing layouts may be wide; **continuous prose** stays ~65–80 characters (~40–50rem). Eyes track poorly on full-bleed paragraphs.
8. **Closed type ladder.** Only **12 · 14 · 16 · 18 · 20 · 24 · 32 · 40 · 48 · 56 · 72**. Intermediates create visual noise and Figma drift.
9. **Hierarchy by size + weight + space, not by color alone.** Headings stay `--ink`. Blue is accent (links, CTAs, stats), not headline paint.
10. **Proximity = belonging (Gestalt).** Related controls share tight gaps (`space-2`–`space-4`); unrelated blocks use section rhythm (`--section-y`). Mis-spacing is a meaning bug.
11. **Rhythm over decoration.** Prefer consistent vertical cadence to extra cards, pills, and shadows. Cards only when they contain an **interaction** or a discrete choice—not as default chrome.
12. **Motion with purpose.** Use motion for hierarchy or feedback (carousel, focus, open/close)—not ambient noise. Prefer reduced-motion respect when adding animation.

### Accessibility & inclusive design

13. **WCAG AA as floor.** Body/UI text contrast ≥ **4.5:1**; large text (≥18px bold / 24px) ≥ **3:1**. `--ink` / `--muted` on `--page` and white-on-`--blue` are chosen for this.
14. **Don’t rely on color alone.** Status, errors, and selected states need text, icon, or pattern—not only hue.
15. **Keyboard & focus are first-class.** Visible focus rings; skip link to `#main` / content; dialogs trap focus and close with Escape (native `<dialog>` where used).
16. **Semantic structure.** One H1 per page; headings in order; buttons for actions, links for navigation; form labels that are real `<label>`s (not placeholder-only).
17. **Touch targets.** Interactive controls aim for ~**44×44px** minimum. Prefer pill buttons with adequate padding over tiny text links for primary tasks.
18. **Plain language.** Short sentences, concrete verbs, no jargon when a simple word works. Prefer periods/commas over em dashes in user-facing eligibility and legal-adjacent copy.
19. **Honest affordances.** Disabled and locked fields look locked; waitlist email prefill that isn’t editable is visually muted (`readonly` / locked styles)—don’t fake editability.

---

## 3. Color

| Token | Hex | Use |
|-------|-----|-----|
| `--ink` | `#0f172a` | Headings & strong text |
| `--muted` | `#1e293b` | Body / secondary text |
| `--text-3` | `#475569` | Captions, footer meta, quiet chrome |
| `--blue` | `#1d4ed8` | Accents only — links, buttons, icons, stats |
| `--blue-deep` | `#1e40af` | Hover / pressed |
| `--blue-ink` | `#0b3a9e` | Deep cobalt surface (optional alt) |
| `--page` | `#ffffff` | Page background |
| `--soft` | `#f4f7fa` | Soft cards / panels / FAQ section ground |
| `--line` | `#e2e8f0` | Borders / rules |
| `--stage-1`…`5` | `#dbeafe` … `#ecfeff` | How-carousel **panel** backgrounds |
| `--surface-1`…`5` | `#2563eb` … `#0e7490` | How-carousel **product mock** fills |

| Step | Panel (`--stage-*`) | Surface (`--surface-*`) |
|------|---------------------|-------------------------|
| 1 | `#dbeafe` | `#2563eb` |
| 2 | `#e0e7ff` | `#4f46e5` |
| 3 | `#ede9fe` | `#7c3aed` |
| 4 | `#e0f2fe` | `#0284c7` |
| 5 | `#ecfeff` | `#0e7490` |

### Why this palette

| Choice | Reason |
|--------|--------|
| Slate ink, not pure black | Softens glare; still high contrast on white |
| Blue as **accent only** | Brand recognition without “everything is a link”; preserves heading seriousness |
| `--soft` off-white | Separates bands (FAQ, cards) without heavy borders—reduces visual fatigue |
| Stage/surface ramps | Step identity in the how-carousel without introducing a second brand color system |
| Avoid purple-on-white / cream-serif / newspaper defaults | Keep ClaimRunner distinct from generic AI-marketing templates |

**Rules:** Headings stay `--ink`. Brand blue is accent, not headline color. `--blue-ink` is a surface.

---

## 4. Type

Only these sizes (px @ 16 root): **12 · 14 · 16 · 18 · 20 · 24 · 32 · 40 · 48 · 56 · 72**

| px | Token | Typical role |
|----|--------|----------------|
| 12 | `--fs-eyebrow` | Kickers, captions |
| 14 | `--fs-sm` | Nav, buttons, secondary UI |
| 16 | `--fs-body` | Body |
| 18 | `--fs-body-lg` | Lead under section H2s |
| 20 | `--fs-lead` | Hero subtext, FAQ questions, logo |
| 24 | `--fs-h3` | Card / about titles |
| 32 | `--fs-h2` | Section H2 (mobile); H3 on desktop |
| 40 | `--fs-metric` / `--fs-stat` | Stat figures |
| 48 | `--fs-h2-lg` | Section H2 (desktop) |
| 56 | `--fs-h1` | Hero H1 (mobile) |
| 72 | `--fs-h1-lg` | Hero H1 (desktop) |

**Fonts:** DM Sans (UI / headings), Source Serif 4 (optional display).  
**Line-height:** tight `1.15` (headings), body `1.6`.  
**Eyebrow tracking:** `0.08em`.

### Why these type choices

| Choice | Reason |
|--------|--------|
| Closed ladder | Prevents “almost the same” sizes; easier Figma ↔ code sync |
| Body 16px | Browser default; accessible baseline; users can still zoom |
| Body line-height ~1.5–1.6 | Comfortable scanning under stress; avoids cramped legal/FAQ feel |
| Tight heading line-height | Display sizes need less leading; keeps hero compact |
| Step at **768px** | Phone keeps H1/H2 restrained; desktop gets presence without a third mid-size |
| Stats in blue at 40 | Number is the message; color encodes “data,” size encodes importance |

### Figma text styles (suggested names)

| Style | Size | Weight | Color |
|-------|------|--------|-------|
| Heading/1 | 56 → 72 @ desktop | Bold 700 | ink |
| Heading/2 | 32 → 48 | Bold 700 | ink |
| Heading/3 | 24 | Bold 700 | ink |
| Body | 16 | Regular 400 | muted |
| Body/Lead | 18–20 | Regular 400 | muted |
| Eyebrow | 12 | Semibold 600 · uppercase | ink / text-3 |
| Stat | 40 | Bold 700 | blue |
| UI/Sm | 14 | Medium 500 | muted |

---

## 5. Spacing

### Token scale (4px grid)

| Token | px | Typical use |
|-------|-----|-------------|
| `--space-1` | 4 | Hairline offsets, icon nudge |
| `--space-2` | 8 | Tight related gaps (label → input) |
| `--space-3` | 12 | Compact stacks inside controls |
| `--space-4` | 16 | Default in-component padding / gap |
| `--space-5` | 24 | Card pad (`--card-pad`), comfortable group gap |
| `--space-6` | 32 | Between subsection blocks |
| `--space-7` | 48 | Strong separation inside a section |
| `--space-8` | 64 | Large internal breaks |
| `--space-9` | 96 | Rare; major chapter breaks |
| `--section-y` | 64→96 | Vertical padding for major homepage sections |
| `--gutter` | ~20–32 | Page edge inset (responsive) |

**Radius:** pill `999` (CTAs, chips), default `16`, card `24`.

### Why a 4px grid

| Principle | Application |
|-----------|-------------|
| **Consistency** | Every gap is a known step—reviewers can say “use space-5” instead of “a bit more” |
| **Optical pairing** | Even steps nest cleanly (8+8=16, 16+8=24) |
| **Density control** | Forms use smaller steps; marketing sections use `--section-y` so the page breathes |
| **Touch & hit area** | Padding on pills/buttons comes from the same scale as layout gaps |

### Spacing theorem

> **Related things sit closer than unrelated things.**  
> If two elements share a task (label + field, headline + lead, primary + secondary CTA), use a small step. If they are different tasks or different sections, jump at least two steps (or use `--section-y`).

Mis-spacing is treated as a bug: it changes what users think belongs together.

---

## 6. Layout: shell vs reading measure

Two different width systems. Don’t conflate them.

| Layer | Token / rule | Value | Job |
|-------|--------------|-------|-----|
| **Page shell** | `--shell` + `.shell` | **1440px** max | Marketing / multi-column layout |
| **Side gutter** | `--gutter` | ~20–32px | Never kiss the viewport edge |
| **Reading measure** | page-specific `max-width` | **~40–50rem** | Long-form prose only |

`.shell` formula: `width: min(100% - (gutter × 2), var(--shell))`.

### Why homepage feels wider than Legal

| Page | Content width | Why |
|------|---------------|-----|
| **Home** | Full `--shell` (1440) | Compositional sections; local text caps still apply (hero lead ~32rem, etc.) |
| **Legal** | `.legal__inner` **50rem (~800px)** | Dense continuous reading; nav/footer still use shell chrome |

Intentional, not a missing breakpoint. Legal may go toward **60rem** if needed; stay under ~**70rem**.

### Breakpoints we use

| Breakpoint | Where | What changes |
|------------|-------|--------------|
| **768px** (`min-width`) | `tokens.css` | Type: H1 56→72, H2 32→48, H3 24→32 |
| **900px** (`max-width`) | `styles.css` | Layout: hide desktop nav links; grids → 1 column; how-panels stack; signup wraps |

Add a third stop only when a layout needs a third behavior.

### Industry reference (not our tokens)

| Approx range | Typical device intent |
|--------------|------------------------|
| &lt; 640px | Phone portrait |
| 640–768px | Large phone / small tablet |
| 768–1024px | Tablet |
| 1024–1280px | Small laptop |
| 1280–1440px+ | Desktop |

Common framework stops: Tailwind **640 / 768 / 1024 / 1280 / 1536**; Bootstrap **576 / 768 / 992 / 1200**. Match **behavior**, not every named breakpoint.

**Rule:** wide shell for marketing UI; narrower measure for legal, FAQ answers, and long body copy.

---

## 7. Page & section patterns (homepage)

| Section | Job | Design notes |
|---------|-----|--------------|
| **Hero** | Brand + promise + CTAs | Full-bleed visual plane; shade for text contrast; primary waitlist, secondary eligibility |
| **Hook / metrics** | Motivate with the problem | One composition; numbers in `--blue`; no fake citation theater |
| **How it works** | Explain the path | Horizontal story; stage colors encode step identity |
| **About** | Values / credibility | Soft cards OK as discrete ideas; keep copy short |
| **FAQ** | Objections & clarity | Soft section ground, white rows; accordion reduces overwhelm |
| **Signup band** | Convert | Single field + primary button; modal for richer waitlist |
| **Footer** | Orient + legal | Explore / get started; Terms → top of `legal.html`; Privacy → `#privacy` |

### Hero budget (hard)

First viewport usually contains only:

1. Brand  
2. One headline  
3. One short supporting sentence  
4. One CTA group  
5. One dominant image / atmosphere  

No detached badges, floating promo chips, or overlays on hero media.

---

## 8. Buttons & interaction

| Style | Fill | Label | CSS | Use |
|-------|------|-------|-----|-----|
| Primary | `button/primary` blue | white | `.btn--solid` | Default CTAs |
| Secondary | transparent | white | `.btn--outline` | On photo / dark hero |
| Monochrome | `button/on-brand` white | `button/on-brand-fg` blue | `.btn--mono` | On dark brand surfaces |
| Quiet | text / minimal | muted | `.btn--quiet` | Tertiary / dismiss |

**Rules:** One primary per view. Pill radius for CTAs (friendly, touchable). Hover uses `--blue-deep`. Modal close uses tertiary icon treatment—not a loud blue disk.

---

## 9. Accessibility checklist (ship bar)

Use when reviewing any marketing or form surface:

- [ ] Skip link present and visible on focus  
- [ ] One H1; heading levels don’t skip  
- [ ] Contrast AA for text and essential UI  
- [ ] Focus visible; order matches reading order  
- [ ] Images that matter have `alt` (decorative = empty alt)  
- [ ] Form fields have associated labels; errors announced in text  
- [ ] Modals: label, close control, Escape, restore focus  
- [ ] Touch targets adequate on primary actions  
- [ ] Page usable when zoomed to 200% without loss of essential content  
- [ ] Color is not the only status cue  

---

## 10. Components (inventory — not a full library yet)

Button (solid / outline / mono / sm / quiet) · Logo · Nav · Kicker · Section H2 · Soft card · Stat card · Form field · Modal · FAQ details · Footer · Carousel controls · Skip link

---

## 11. How to copy into Figma (manual)

1. Open a Design file → **Local variables**.  
2. Collections e.g. `ClaimRunner / Color` and `ClaimRunner / Space`.  
3. Color variables from the tables above.  
4. Spacing as Number/Float (4, 8, 12…).  
5. Text styles from the type table; bind fills to color variables.  
6. When tokens change in code, update Variables — **code wins**.

---

## 12. How we sync (this repo)

- **Tokens:** `tokens.css`  
- **Rationale + rules:** this file  
- **Figma:** [Claim-runner-design](https://www.figma.com/design/5t3zYwu6uAStoPffTUrPOG/Claim-runner-design)  
  - **Primitives** — raw ramp hexes  
  - **Semantic** — `text/*`, `surface/*`, `stage/*`, `button/*` → aliases; WEB → `var(--…)`  
  - **ClaimRunner / Space · Radius · Type**  
- **Living page:** `index.html` + `styles.css`

### Semantic ↔ CSS map (colors)

| Semantic | CSS |
|----------|-----|
| `text/heading` | `--ink` |
| `text/body` | `--muted` |
| `text/tertiary` | `--text-3` |
| `text/accent` | `--blue` |
| `action/hover` | `--blue-deep` |
| `surface/brand-deep` | `--blue-ink` |
| `surface/white` | `--page` |
| `surface/card` / `surface/subtle` | `--soft` |
| `stroke/default` | `--line` |
| `stage/1`…`5` | `--stage-1`…`5` |
| `surface/1`…`5` | `--surface-1`…`5` |
| `button/primary` | `--blue` |
| `button/on-brand` | white fill on cobalt CTA band |
| `button/on-brand-fg` | `--blue` label on that fill |

---

## 13. Decision log (keep short)

| Decision | Choice | Why |
|----------|--------|-----|
| Shell width | 1440px | Fits modern desktop marketing without ultrawide stretch |
| Legal measure | 50rem | Reading comfort for Terms/Privacy |
| Type step | 768px | Phone vs desktop presence |
| Layout collapse | 900px | Grids/nav need earlier reflow than type |
| Primary CTA | Waitlist | Product not fully open; capture interest honestly |
| Eligibility | Secondary CTA | Useful now; not the only north star |
| FAQ ground | `--soft` | Separates from white marketing bands; white accordion rows for focus |
| Footer cites | Removed | Dummy cites undermine trust |
| Disclaimer footer link | Removed | Covered in legal body; reduce footer clutter |
| Terms link | Top of `legal.html` | Land on document start, not mid-page hash |
