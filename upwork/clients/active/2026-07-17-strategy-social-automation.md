---
name: strategy-social-automation
sensitivity: private
platform: direct (school contact)
status: discovery
created: 2026-07-17
---

# Client: Strategy Social Automation (Business unnamed)

**Business:** Unknown — business strategy consulting/content brand (confirmed topic areas below)
**Platform:** Direct. School contact introduced Emmanuel to end client. Not through Oba.
**Middleman:** School friend passes messages between Emmanuel and end client
**Pay:** $200 fixed. Emmanuel keeps 100% (friend giving his full cut)

---

## Project Scope

Daily social media automation tool that generates business strategy content, presents it for approval via Telegram, then posts to social platforms automatically.

**Cron trigger:** 9:00 AM daily

**Platforms confirmed:** Instagram, LinkedIn (with image), others TBD

**Content specs:**
- Max 75 words per post
- Text + image (Instagram and LinkedIn require matching image)
- Dynamic CTA based on content relevance to the business services
- CTA points to their contact form

**Content topic areas:**
- Business case studies: who won, why, how
- Definition of strategy: ideas, misconceptions, myths
- Strategy development process
- Business nuggets: strategy, people, finance, org structure, culture, team management
- Disruption and innovation
- Competition in business
- Leadership
- Succession planning
- Strategy execution

---

## Stack Decided

| Layer | Tool |
|---|---|
| Trigger | n8n cron node (9:00 AM daily) |
| Content generation | Claude API (recommended) or OpenAI GPT-4 |
| Image generation | Kie AI (image models) |
| Approval flow | Telegram bot in n8n (approve/cancel/edit) |
| Social posting | Upload-Post ($16/month) |

**Why Upload-Post over Blotato:** Upload-Post ($16/month) covers same platforms with official n8n node. Blotato ($29/month) adds AI content features we don't need since Claude handles generation. $13/month cheaper with identical posting capability.

**LLM recommendation:** Claude API. Same price range as OpenAI at this volume (~$5-15/month daily posting). Slightly stronger reasoning for nuanced strategy content.

---

## Monthly Running Costs

| Tool | Cost |
|---|---|
| n8n Cloud Starter | $24/month |
| Claude API | ~$5-15/month |
| Kie AI credits | Already available (from existing bundle) |
| Upload-Post Basic | $16/month |
| **Total estimate** | **~$45-55/month** |

---

## Approval Flow Design

1. Cron fires at 9AM
2. Claude generates 75-word post + picks CTA
3. Kie AI generates matching image
4. Telegram bot sends text + image to approver
5. Approver replies: approve / cancel / edit
6. Edit: bot collects revised text, re-presents
7. Approve: posts to all confirmed platforms simultaneously

---

## Discovery Questions Sent (Awaiting Response)

1. Which platforms beyond Instagram and LinkedIn? (Facebook, Twitter, others?)
2. What does the business do and what services does it offer? (for CTA accuracy)
3. Contact form link
4. Instagram Business account already connected to a Facebook Page?
5. Brand assets: logo, colors, preferred image style
6. One person approving on Telegram or does a team need to review?

---

## Key Notes

- Instagram API requires Facebook Business account + Instagram Business account linked to a Facebook Page. Most complex setup step. Must confirm client has this before build starts.
- This is Emmanuel's own job. No Oba involvement. Full $200 retained.
- Business name and service details needed before any content generation can be configured.
