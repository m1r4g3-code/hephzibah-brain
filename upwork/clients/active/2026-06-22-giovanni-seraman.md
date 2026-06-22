---
sensitivity: private
entity_type: person
name: "Giovanni"
company: "SERAMAN"
platform: "Fiverr"
website: "shop.seraman.com"
email: "seraman.adv@gmail.com"
country: "Italy"
category: "Tactical / Military Gear (sunglasses, boots, medical equipment)"
status: "active"
quality_score: 90
introduced_by: "Oba (Adelaja O.)"
---

## Client Overview

Giovanni runs SERAMAN — an Italian tactical and military gear brand selling products like sunglasses (Gator Spectre), boots (AKU Tactical), bandages, and other gear via shop.seraman.com. He was originally a freelancer client of Oba's, who introduced the automation opportunity.

## Project: AI Video Production System

**Platform:** Fiverr (via Oba's account — 50/50 split)
**Status:** Milestone 1 complete. Milestone 2 in progress.

**What was built:**
Full automated pipeline — Tally Form → n8n → Claude AI (Italian script) → Kie AI Veo 3.1 (video generation, dual-branch parallel) → Creatomate (video assembly + captions) → Blotato (social publishing to 4 platforms) → branded email notifications (success + error). Google Sheets tracks every run across 3 sheets.

**Architecture highlights:**
- Dual-branch parallel Kie AI generation (Branch A: scenes 1+8, Branch B: scenes 2-7)
- Async state machines, retryCount 20, regenCount 3 per scene
- item-identity integrity — scene_number travels explicitly through all nodes
- Claude v4 trust-first prompt (Product → Experience → Feature → Benefit)
- 4 modular n8n workflows: Product Automation, Generate Videos, Edit Videos, Error Handler

## Financials

| Milestone | Amount | Status |
|---|---|---|
| Milestone 1 | $1,000 | Delivered — 5-star review |
| Milestone 2 | $1,000 | In progress |
| Long-form pipeline (5–8 min) | $1,500 | Scoped, not started |

**Total potential:** $3,500+

## Review (Milestone 1)

> "Excellent work, fast and super professional. Perfect communication. They were able to produce what I asked for, modifying it as requested. Delivery was early. Highly recommended!!!"
> — Seller communication: 5 | Quality: 5 | Value: 5

## Flags

- **Green:** Pays, reviews promptly, clear feedback, expanding scope
- **Green:** Italian speaker — product content stays in Italian
- **Green:** Long-form project already scoped at $1,500
- **Watch:** Blotato posting failed once (execution 279, "Call Seraman Post to Socials") — social publishing still being confirmed

## Tech Stack (Giovanni's side)

- Kie AI credits (pay-per-use, no subscription)
- Creatomate ~$29/mo
- Blotato $29/mo
- n8n (self-hosted or cloud)
- Google Sheets (being migrated to his own account for M2)
- Tally form: https://tally.so/r/obx5vx

## Handoff

Handoff doc generated: `outputs/strategy/2026-06-22-seraman-handoff-v1.pdf`
Includes: workflow architecture screenshots, Google Sheet breakdown, email alert examples, engineering depth, running costs, Italian closing message.
