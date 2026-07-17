---
name: madson-children-animation
sensitivity: private
platform: fiverr
status: discovery
created: 2026-07-17
---

# Client: MadSoN — AI Children's Animation Studio

**Business:** Children's animated content creator (social media focus)
**Platform:** Fiverr (Oba's gig)
**Client type:** New to Fiverr, price-sensitive but vision-clear, trust problem not budget problem

---

## Project Vision

Fully automated children's cartoon production pipeline triggered from Telegram. Client sends a message, pipeline generates script, character options, 3-minute video with music and optional voiceover, and delivers the finished video.

---

## Stack Decided

| Layer | Tool |
|---|---|
| Trigger + Delivery | Telegram + n8n native node |
| Orchestration | n8n Cloud |
| Script generation + Scene breakdown | Claude API (HTTP node in n8n) |
| Character generation + Video clips | Kie AI (Veo 3 Fast + image models) |
| Voiceover | ElevenLabs |
| Music | Suno API |
| Final assembly | Creatomate |

**Ruled out:** Claude Code (not needed — they need Claude API), Shotstack (replaced by Creatomate), Trello (unnecessary overhead — Telegram is the interface, n8n is the control layer), Runway/Luma/Midjourney (all replaced by Kie AI)

---

## Estimated Monthly Running Costs

| Tool | Cost |
|---|---|
| n8n Cloud Starter | $24/month |
| Kie AI credit bundle | $50/month |
| Creatomate Essential | $41-54/month |
| ElevenLabs | $11-22/month |
| Suno API | ~$10-30/month |
| Claude API | ~$10-20/month |
| **Total** | **~$146-200/month** |

---

## Pricing

**Floor:** $2,500
**Recommended:** $3,000-3,500
**Rationale:** 4x more complex than Elbert pipeline. Interactive Telegram bot with multi-step approval, 18-36 clips per episode, character generation layer, multi-API orchestration. Elbert was $1,200-1,500 for 2 clips and Drive delivery.

**Asset framing to use:**
"You pay once to build the studio. Every episode after that costs only the tool subscriptions. At 20 episodes per month the per-episode cost drops to $7. Price goes down forever as volume goes up."

**Monthly cost closes the argument:** If he cannot afford the build fee, he cannot afford to run it.

---

## Client Behavior

- New to Fiverr
- Proposed $10-11/hr x 10hrs/day x ~20 days = ~$2,000 max
- Wants hourly (avoid — no clear deliverable, client can cap hours)
- Psychology: scared of being duped, not actually broke
- Fix: milestone payments + Week 1 checkpoint + proof of similar work (Elbert/SERAMAN)
- Hold price. Push fixed-price milestones, not hourly.

---

## Discovery Questions Sent (Awaiting Response)

1. Same recurring characters across episodes or fresh each time?
2. Voiceover narration or music only?
3. How many episodes per month at full volume?
4. Approve character designs before video generates, or fully automated?
5. What budget range for the build?

**Most critical question:** Recurring vs fresh characters. Consistent character across 36 clips = harder architecture. Determines the full build scope.

---

## Status

- Discovery questions sent via Oba
- MadSoN has not responded yet
- No proposal built yet
- Awaiting answers before scoping or pricing conversation

---

## Key Lesson

Same asset pricing principle as Elbert applies here at higher tier. This is a production studio, not a per-video service. Price reflects lifetime value of the asset.

[[automation-asset-pricing]] [[elbert-savvysox]]
