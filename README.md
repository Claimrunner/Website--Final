# ClaimRunner homepage handoff (v8)

Static reference for implementing the **marketing homepage** on the official frontend. Not a production backend. Eligibility checker is **out of scope** for this package.

Open `index.html` in a browser, or from this folder:

```
npx serve -l 5174 .
```

Then: http://localhost:5174/

## What to implement

| Surface | File | Notes |
|---------|------|--------|
| Homepage | `index.html` | Hero, metrics, how-carousel, Mission/Background, FAQ, waitlist band, footer |
| Waitlist modal | `#waitlist-modal` | Opens from Join the waitlist / Join the list. Email from the inline form is prefilled and locked. |
| Contact modal | `#contact-modal` | Opens from footer Contact. Name and email required. Message optional. |
| Legal | `legal.html` | Terms + Privacy. Same waitlist and contact modals. |
| Tokens | `tokens.css` | Color, type ladder, space, radius. Do not invent mid sizes. |
| Page CSS | `styles.css` | Imports tokens. Buttons, layout, carousel, modals. |
| Foundations | `FOUNDATION.md` | Why the tokens exist. Use when mapping to Figma or a design system. |
| Hero image | `assets/hero-placeholder.jpg` | Cropped with `60% top` so the head stays in frame. |

## Modals

Native `<dialog class="modal">`. Backdrop click, X, and Cancel (contact only) close them.

- Close control is Phosphor **x-circle**: regular at rest (`--text-3`), fill on hover (`--ink`). Same swap as carousel arrows (those use brand blue).
- The dialog element must stay `background: transparent` with matching `border-radius`, and `dialog:modal { overflow: visible }`, or square grey corners show around the rounded sheet.
- Waitlist and contact share `.modal` / `.modal__sheet` / `.modal__form`. Do not restyle one without the other.
- Forms currently `preventDefault` and close. Wire to the real waitlist / contact endpoints.

## How carousel

Five snap panels. Controls are Phosphor circle-arrows, regular at rest, fill on hover, brand `--blue` / `--blue-deep`. Last panel needs extra `padding-right` on the track so it aligns to the same left edge as panels 1–4 (already in `styles.css`).

## Copy and product rules

- ClaimRunner is not a law firm. Do not imply legal advice, predicted outcomes, or guaranteed results.
- Primary CTA is waitlist (solid blue). Eligibility is secondary (outline). Eligibility UI is not in this zip.
- User-facing copy: no em dashes.
- Type is a closed ladder. See `FOUNDATION.md`.

## Out of scope

Eligibility v1/v2, compare boards, and internal draft nav. The homepage still has a "Check your eligibility" button; leave it as a link to the future eligibility route.

## Version

This is **v8** (was `homepage-mission-test`). The previous current homepage is archived as v7 and is not in this zip.
