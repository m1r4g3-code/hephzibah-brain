---
sensitivity: private
entity_type: brand
name: Hephzibah Design System
last_updated: 2026-08-08
version: 2
---

# Hephzibah Design System — v2 "Paper"

**v1 was dark, glossy, and decorated.** Rejected 2026-08-08: it looked like every AI-startup landing page, the type sizes were chosen per-template rather than from a scale, and an accent bar sat under every headline meaning nothing. Decoration was doing the work design should have done.

**v2 is paper.** White, a neutral grey ramp, near-black ink, and lemon used rarely and only where it carries meaning.

---

## Why White Is The Strategic Choice

Every gadget page in Lagos is dark, neon, emoji-heavy, and shouting. That is the visual default of the market.

**A white, quiet, typographic brand is instantly distinguishable from all of them** — before a single word is read. That is free differentiation, and it maps exactly onto the position in [[trust-as-margin]]: the seller who does not need to shout.

White also carries an implicit claim that dark cannot: **nothing is hidden.** Dark backgrounds flatter poor product photography and conceal edges. White exposes everything — which is the correct visual metaphor for a business whose entire product is disclosure.

---

## Foundations

### Colour — semantic roles, not a swatch list

Every colour has one job. Referring to `--ink-2` rather than "grey" is what stops the ramp drifting over time.

```
SURFACES                              CONTENT
--paper      #FFFFFF   base           --ink     #0E0E0C  display, headlines
--surface-1  #FAFAF9   raised         --ink-1   #26262340 body
--surface-2  #F4F4F2   sunken fill    --ink-2   #6B6B66  secondary
--surface-3  #EAEAE7   deep fill      --ink-3   #A3A39D  tertiary, labels
--ink-inv    #FFFFFF   on dark

LINES                                 ACCENT
--line       #E6E6E2   hairline       --lemon      #E4F543  matte lemon
--line-2     #D6D6D1   defined        --lemon-ink  #0E0E0C  text ON lemon
--line-3     #BDBDB7   strong
```

The greys are **warm neutrals**, not cool. Cool grey reads as software chrome; warm grey reads as paper and stock, which is the register this brand wants.

**The near-black is `#0E0E0C`, never `#000000`.** Pure black against white is a contrast level no printed material achieves; it reads as harsh and cheap on screen.

### The lemon rule — the most important rule in the system

**Lemon never carries text on a light surface.** `#E4F543` on white is roughly 1.3:1 contrast — invisible.

Lemon appears in exactly three forms:

| Form | Use | Rule |
|---|---|---|
| **Fill** | A solid block or pill with `--lemon-ink` text on it | Text on lemon is always near-black |
| **Rule** | A 3–4px bar or underline | Never longer than the text it marks |
| **Dot** | A 6–8px status marker | One per surface |

**Once per surface. Never twice.** If two things are lemon, neither is important.

And lemon marks **the single most important fact on the piece** — a verified battery figure, the price, the one-line promise. Never a decoration, never a divider, never "brand colour applied here."

### Type — one family, a fixed scale

**Inter** for everything structural. **Caveat** for the human annotation only — a note in Emmanuel's own voice, never a heading.

The scale is fixed. A size not on this list does not get used.

| Token | Size / line | Tracking | Weight | Use |
|---|---|---|---|---|
| `display-1` | 104 / 0.94 | −0.045em | 700 | Flyer hero |
| `display-2` | 72 / 0.96 | −0.04em | 700 | Card hero |
| `display-3` | 52 / 1.0 | −0.035em | 700 | Product name |
| `title-1` | 36 / 1.15 | −0.02em | 700 | Section head |
| `title-2` | 26 / 1.25 | −0.015em | 700 | Sub-head |
| `body-1` | 20 / 1.5 | −0.006em | 400 | Lead paragraph |
| `body-2` | 17 / 1.55 | −0.003em | 400 | Body |
| `mono-num` | 30 / 1 | −0.02em | 700 | Spec figures |
| `label` | 12 / 1 | +0.16em | 600 | Uppercase labels |
| `micro` | 11 / 1.4 | +0.04em | 400 | Legal, timestamps |

**Tracking scales inversely with size.** Large type needs negative tracking or it looks loose; uppercase labels need positive or they look cramped. Applying one global letter-spacing is the single clearest sign a system was not designed.

### Space — 4pt grid

`4 · 8 · 12 · 16 · 24 · 32 · 48 · 64 · 96 · 128 · 160`

Nothing off-grid. If a gap looks wrong, the fix is the next step on the scale, not an arbitrary number.

**Vertical rhythm beats horizontal decoration.** Space between blocks is what creates hierarchy — not lines, not boxes, not background fills.

### Radius

`6 (chip) · 10 (control) · 16 (card) · 22 (media) · 999 (pill)`

### Elevation

**There is none.** No drop shadows anywhere. Depth is expressed with surface tone and hairlines. A shadow on a white system reads as a 2014 Material app.

---

## Layout

### Margins scale with canvas, not with taste

| Canvas | Margin | Column gutter |
|---|---|---|
| 1080×1350 card | 64 | 24 |
| 1080×1920 story | 80 | 24 |
| 2480×3508 A4 | 190 | 48 |

### The rules that do the work

1. **One idea per surface.** If a graphic makes two points it makes neither.
2. **Left-aligned, ragged right.** Centred type is for ceremony; this brand is informational.
3. **Optical alignment beats mathematical.** Large display type needs a negative left offset (≈ −0.05em) so its stem aligns with the text below it, because glyph side-bearings lie.
4. **Product photography is the hero.** Where a photo exists it gets the largest area on the surface. Type serves it.
5. **Whitespace is not empty.** The gap above a price is what makes the price loud.

---

## Components

**Spec row** — label in `label` grey above the figure in `mono-num` ink. Separated by hairlines, never boxes. Verified figures may take the lemon rule; unverified never do.

**Verification badge** — a pill. Verified: lemon fill, near-black text, small dot. Unverified: `surface-2` fill, `ink-2` text, no accent anywhere.

**Price block** — `display-2`, ink, with terms in `micro` beneath at `ink-3`. Never boxed, never coloured. The size does the work.

**Flaw note** — `surface-2` fill, no border, `label` heading in ink-2, body in `body-2`. Deliberately quiet: it is honest, not apologetic.

**Wordmark** — `H` in a 2px near-black rounded square, name in `label` tracking. Monochrome always. The wordmark never takes the accent.

---

## What This System Forbids

- Gradients used as decoration
- Glow, drop shadow, bevel
- Background grids, dot patterns, "tech" texture
- More than one accent element per surface
- Lemon behind or as text on white
- Any type size not on the scale
- Centred body copy
- Emoji in brand-owned surfaces
- Pure black or pure-white text on tinted fills

---

## The Apple Question — Sensibility, Not Assets

Emmanuel asked about using Apple's design system. The answer is to take the **sensibility** and never the assets.

**Not the assets:** SF Pro is licensed for Apple-platform development, not third-party marketing. And visually, a reseller dressed as Apple looks like a reseller pretending to be Apple — which is an implied affiliation that does not exist, and therefore exactly the sort of unverifiable claim this brand is built against.

**The sensibility, absolutely:** enormous whitespace, very few elements, one idea per surface, product as hero, type doing the hierarchy work instead of boxes and colour, obsessive optical precision.

Those principles are not Apple's property. They are simply what restraint looks like, and this system now applies them.

---

## Linked

[[gadget-brand]] · [[trust-as-margin]] · [[listing-framework]] · [[content-strategy]]
