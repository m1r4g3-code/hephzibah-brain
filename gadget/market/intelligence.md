---
sensitivity: private
entity_type: domain
name: Market Intelligence — Running Log
last_updated: 2026-08-08
---

# Market Intelligence — Running Observation Log

Append-only. Every market signal worth remembering gets a dated entry. Three entries pointing the same direction is a pattern — promote it to `patterns/winning-products.md` or `patterns/dead-stock.md`.

**What counts as a signal:** a price move, a supply change, a demand shift, a competitor action, a policy or FX change, a repeated buyer question. Not opinions. Observations with dates.

---

## Entry Format

```markdown
### YYYY-MM-DD — [one-line headline]
**Type:** demand | supply | price | competitor | policy | fx | buyer-behaviour
**Category:** [affected category]
**Observation:** What was actually seen. Source. Numbers if there are any.
**So what:** What this changes about a decision. If nothing — do not write the entry.
**Confidence:** high (verified) | medium (single source) | low (rumour, needs checking)
```

The **So what** line is the whole point. An observation that does not change a decision is noise, and a log full of noise stops being read.

---

## Standing Market Structure

Baseline conditions this business operates in. Reviewed monthly, not appended to daily.

**The FX transmission lag.** Retail gadget prices in Lagos follow the parallel rate up within days and come down slowly, over weeks. That asymmetry is the single biggest margin lever available: stock bought at a good rate and sold into a risen market carries the entire FX move as profit. The inverse is equally true and is how gadget businesses die — holding stock bought high into a strengthening naira. **Do not carry more than 3 weeks of stock in a rising-naira window.**

**"UK used" is an unregulated term.** It signals imported second-hand, nothing more. Grade, battery health, and repair history vary completely between two units sold under the same words. This ambiguity is precisely the gap the Hephzibah brand exists to close — see `identity/brand.md`.

**Demand is calendar-shaped.** December (salaries, bonuses, gifting) is the peak. January is the trough — money is gone, school fees are due. iPhone launch (Sept/Oct) drops the resale value of the previous two generations by 10–20% within weeks. Plan inventory against both.

**The counterfeit floor.** For AirPods, chargers, and power banks, fakes are so widespread and so good that buyers assume fake by default. This is a moat, not a problem: a seller who can *prove* genuine takes the whole premium segment.

**Trust is the actual scarce resource.** Nigerian buyers have all been burned or know someone who has. This is why referral converts at a multiple of cold traffic, and why one public failure costs more than ten quiet wins earn.

---

## Observation Log

### 2026-08-08 — Domain initialised
**Type:** policy
**Category:** all
**Observation:** Gadget OS built. No market observations logged yet. Log is empty by design, not by oversight.
**So what:** The first ten entries should come from the operator's existing head knowledge — things Emmanuel and Yemi already know but that live nowhere the OS can read. Until then, every market-demand score `qualify.py` produces is reasoning from first principles rather than from data.
**Confidence:** high

---

<!-- Append new entries above this line, newest first. -->

## Signals Worth Checking Weekly

| Signal | Where | Why |
|---|---|---|
| Parallel USD/NGN rate | AbokiFX or trusted BDC | Every import cost and every re-price decision |
| Computer Village asking prices — top 5 SKUs | Yemi, in person | Detects supply gluts and shortages before they show in retail |
| Jiji listing counts for anchor SKUs | jiji.ng search | Listing count is the best available competition proxy |
| Competitor page posting frequency | IG/X | A page that stops posting is a page losing money |
| Apple/Samsung launch calendar | Announcements | Launch drops the previous generation 10–20%. Clear stock ahead of it. |
| Repeated buyer questions | Own DMs | The question asked three times is the thing missing from every listing |

---

## Linked

[[gadget-index]] · [[gadget-competitors]] · [[winning-products]] · [[dead-stock]]

### 2026-08-22 — iPhone 18 launch window opens in about three weeks
**Type:** supply / price
**Category:** phones
**Observation:** Apple's compare page confirms the iPhone 17 line (17, 17 Pro, 17 Pro Max, Air, 17e) as current. Nothing about an iPhone 18 is announced. Bloomberg and analyst reporting points to a keynote around 9 September 2026 with retail from roughly the 18th, unconfirmed by Apple. Reporting also says the lineup SPLITS: only the 18 Pro and Pro Max in September plus a first foldable, with the standard 18 and 18e pushed to spring 2027.
**So what:** Two consequences, one commercial and one for stock.

1. **Content.** "Buy now or wait" is answerable honestly and differently per buyer. Pro buyers should wait three weeks. Everyone else should not, because the next standard iPhone is over six months out. Carousel published 2026-08-22.
2. **Own exposure.** Ten iPhone Air units and the 17-series stock sit in front of a launch window. Our own dead-stock note says no bulk commitment within six weeks of a successor announcement. That window is now open, and these are broker units so the risk is a stale posted price rather than trapped capital, but the vendor's price will move.

**Measured from the ladder, not assumed:** one generation of age costs about 5% (17 → 16, ₦820k → ₦780k). Two generations costs about 26% (17 → 15, ₦820k → ₦610k). So a launch does not crash last year's phone; it moves the two-year-old model into being the value pick. That is the honest advice to give a budget buyer.
**Confidence:** high on the iPhone 17 line and on the ladder figures. Medium on the September dates and the split, which are reporting rather than Apple.
