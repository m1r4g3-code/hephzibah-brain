---
sensitivity: private
entity_type: domain
name: Gadget Niche — Categories In and Out
last_updated: 2026-08-08
status: DEFAULT — needs operator confirmation (queue g001)
---

# Niche — What Hephzibah Gadgets Sells

> **⚠️ This file ships with a researched default, not confirmed operator data.**
> `qualify.py` reads the brand-fit weighting from this file. Until Emmanuel and Yemi confirm the tables below, every brand-fit score the OS produces is a guess with a confident face on it. Queue item `g001`.

---

## The Thesis

Sell devices where **the buyer's biggest fear is being cheated, and where inspection can remove that fear.**

That single sentence decides category selection. It is why used phones are in and cheap Bluetooth speakers are out. On a ₦450k used iPhone, verified battery health and a named flaw are worth real money to the buyer — they are buying certainty. On a ₦6k speaker, nobody is afraid, nobody will pay for certainty, and the margin cannot fund the inspection time.

**Corollary: high ticket, low unit count.** Ten devices at ₦80k margin beats two hundred at ₦4k. Two hundred units is two hundred conversations, two hundred deliveries, and two hundred chances for something to go wrong — for the same money.

---

## Categories IN

| Category | Examples | Why it fits | Typical ticket (₦) |
|---|---|---|---|
| **Used premium phones** | iPhone 11–15, Samsung S-series, Pixel | Core category. Fear is highest, inspection value is highest, ticket is highest. | 200k – 900k |
| **New sealed phones** | Current-gen iPhone, Samsung A/S | Lower margin but builds the premium frame. Anchors the brand. | 400k – 1.5m |
| **Premium audio** | AirPods Pro/Max, Sony WH/WF, Bose | Heavy counterfeit market → verification is worth real money. Compact, ships easily. | 60k – 350k |
| **Power & charging** | Anker/Baseus banks, GaN chargers, MagSafe | Genuine-vs-fake matters, buyers get burned constantly, repeat purchase. | 15k – 90k |
| **Wearables** | Apple Watch, Galaxy Watch | Same fear profile as phones. Battery health is the whole decision. | 80k – 400k |
| **Laptops (selective)** | MacBook Air/Pro, ThinkPad, XPS | Highest ticket in the range. Only with full diagnostic report. | 400k – 2m |
| **Accessories (attach only)** | Cases, screen protectors, cables | Never the headline. Sold attached to a device at point of sale. | 3k – 25k |

## Categories OUT

| Category | Why it is out |
|---|---|
| **Generic no-brand audio** | Ticket too low to fund inspection. No fear to relieve. Pure price competition. |
| **Cheap Android (<₦80k)** | Margin thin, return rate high, buyer is price-only. Wrong customer entirely. |
| **Drones** | Import complexity, NCAA regulation exposure, fragile, tiny local market. |
| **Large appliances / TVs** | Freight and breakage kill the margin. Wrong logistics profile completely. |
| **Gaming consoles** | Margin compressed by grey-market volume. Warranty claims are brutal. |
| **Vapes / e-cigs** | Brand gate. Does not belong on a name-bearing brand. |
| **Smart home (Alexa/Nest)** | Weak local demand. Needs support Hephzibah cannot provide. |
| **Anything counterfeit or "grade AAA replica"** | Absolute. The entire brand is built against this. No margin justifies it. |
| **Stolen / IMEI-blacklisted devices** | Absolute. Every unit gets an IMEI check before purchase, no exceptions. |

---

## The Brand-Fit Score — How `qualify.py` Reads This

`brand_fit` is 15% of the composite. Score it against these:

| Signal | Points |
|---|---|
| Category is in the IN table | +40 |
| Ticket ≥ ₦60,000 | +15 |
| Verifiable condition attributes exist (battery %, IMEI, serial, cycle count) | +15 |
| Recognised brand a buyer already trusts | +10 |
| Repeat-purchase or attach potential | +10 |
| Photographs well in the Terminal Precision style | +10 |
| **Category is in the OUT table** | **Score 0. Hard stop.** |

Score 0 on brand fit → the composite is irrelevant. Skip.

---

## Depth Over Breadth

Same logic that ranks a freelancer #1 for one keyword ranks a gadget vendor as *the* person for one category.

**"Where do I get a used iPhone I can trust?"** is a question with an answer. **"Where do I get gadgets?"** is not a question anyone asks.

Rules:
1. **One anchor category at a time.** Used premium phones is the anchor. Everything else is adjacent, not parallel.
2. **Adjacent expansion only.** Phones → phone accessories → audio → wearables. Each step shares the buyer. Do not jump to laptops until phones are consistently profitable.
3. **Content follows the anchor.** If the anchor is used iPhones, content is about used iPhones — battery health, grades, what "UK used" actually means. Not a general gadget feed.
4. **Rotation is a decision, not a drift.** Category rotation only via `/war-room`. Logged here with the date and the reason.

---

## Category Rotation Log

| Date | Change | Reason | Outcome |
|---|---|---|---|
| 2026-08-08 | Initial set defined (default) | OS foundation build. Inferred from operator context, not confirmed. | Pending confirmation — `g001` |

---

## Linked

[[gadget-index]] · [[gadget-brand]] · [[gadget-pricing]] · [[product-qualification]]
