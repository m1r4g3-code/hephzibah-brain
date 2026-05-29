---
sensitivity: private
entity_type: domain
name: Active Upwork Profile State
last_updated: 2026-05-29

account_owner: "partner"
badge: "rising_talent"
jss: null
rate_usd: 20
total_reviews: 0
total_earned_usd: 0

title: "AI Automation & Workflow Specialist | n8n | Claude API | No-Code"

overview_keywords:
  - "automation"
  - "n8n"
  - "workflow"
  - "AI"
  - "Claude"

portfolio_items:
  - title: "(none yet)"
    category: "none"
    tools: []

skills_listed:
  - "n8n"
  - "AI Automation"
  - "Claude API"
  - "Workflow Automation"
  - "API Integration"
---

# Active Upwork Profile — State Document

Source of truth for the active Upwork profile. `qualify.py` reads this to score profile-job fit. Update it immediately after any profile change.

## How to update

- **New portfolio item** → add entry to `portfolio_items`
- **Rate changed** → update `rate_usd`
- **New review / JSS appears** → update `jss`, `total_reviews`, `total_earned_usd`
- **Badge changes** → update `badge`
- **Account switches** → update `account_owner`, reset/update all fields

## Rate ladder log (append only)

- 2026-05-29 | $20/hr | baseline — Rising Talent, 0 reviews

## Current account notes

Partner account, 50/50 split. Handback ~June 2026. Emmanuel's own account launches then at $40/hr minimum.
