---
name: madson-children-animation
sensitivity: private
platform: fiverr
status: proposal_sent
created: 2026-07-17
updated: 2026-07-17
---

# Client: MadSoN — AI Children's Animation Studio

**Business:** Children's animated content creator (social media focus)
**Platform:** Fiverr (Oba's gig)
**Client type:** New to Fiverr, price-sensitive but vision-clear, trust problem not budget problem

---

## Project Vision

Fully automated children's cartoon production pipeline triggered from Telegram. Client sends an episode brief, pipeline generates script, character options, 3-minute video with voiceover narration and music, and delivers the finished video. Full multi-stage approval at every step.

---

## Discovery Answers Received (2026-07-17)

1. **Characters:** Consistent across ALL episodes. Client controls when to upgrade. This is the hardest architecture constraint — character reference system required.
2. **Audio:** Both voiceover narration AND music confirmed. ElevenLabs + Suno both in scope.
3. **Volume:** 100 videos/month at full capacity. 3-minute videos. This changes running cost math significantly.
4. **Approval:** 4-stage approval per episode via Telegram (described below). "Every stage requires my approval."
5. **Budget:** Asked for total fixed price. Opened the door to us naming the number.
6. **Bonus scope:** Also interested in music video editing (providing footage angles, lighting cues, per-moment instructions). Scoped as Phase 2.

---

## Stack Decided

| Layer | Tool |
|---|---|
| Trigger + Delivery | Telegram + n8n native node |
| Orchestration | n8n Cloud |
| Script generation + Scene breakdown | Claude API (HTTP node in n8n) |
| Character generation + Video clips | Kie AI (Veo 3 Fast + image models) |
| Character consistency | Reference image system (locked reference injected into every generation) |
| Voiceover | ElevenLabs |
| Music | Suno API |
| Final assembly | Creatomate |

**Ruled out:** Claude Code (not needed), Shotstack (replaced by Creatomate), Trello (unnecessary), Runway/Luma/Midjourney (replaced by Kie AI)

---

## Character Consistency Architecture

**What we build:** Reference image system.
- First session: client describes character, AI generates 4-6 image options, client selects one
- That approved image is stored and injected as a reference into every future generation call
- Consistency: ~75-85% (same design, colors, style across episodes; minor variation between clips)
- Limitation disclosed: not pixel-perfect. Current ceiling of AI video generation.
- Upgrade path (not in scope): custom character LoRA training for 95%+ consistency (different project, different timeline)

**At 100 videos/month with 18-36 clips per video = 1,800-3,600 individual clip generations/month.** Variation will be visible. Client acknowledged.

---

## Approval Flow (4 Stages Per Episode)

1. Client submits episode brief via Telegram → Claude generates script → sent to client for approval or edit
2. Character reference displayed for confirmation before scene generation begins
3. Generated clips previewed before assembly
4. Assembled video presented before final delivery

At 100 videos/month: ~400 approval interactions/month on client's end. Disclosed upfront.

---

## Estimated Monthly Running Costs at Scale (100 videos/month)

| Tool | Cost |
|---|---|
| n8n Cloud | $24-50/month |
| Kie AI (2,500+ clips at ~$0.20-0.40/clip) | $400-800/month |
| Creatomate (100 renders) | $100-150/month |
| ElevenLabs (at this volume) | $22-50/month |
| Suno API | $20-30/month |
| Claude API (scripts) | $15-30/month |
| **Total** | **~$580-1,100/month** |

Client holds these subscriptions directly.

---

## Pricing

**Quoted:** $3,500 fixed price (sent in discovery response)
**Covers:** Full cartoon pipeline, 4-stage Telegram approval, character consistency system, voiceover + music, Phase 1 delivery
**Running costs disclosed:** $600-1,000/month at 100 videos/month
**Payment terms:** 50% before build, 50% on delivery and handoff
**Phase 2 (music video editing):** Separate scope and quote after Phase 1

**Pricing rationale:**
- 4x more complex than Elbert ($1,500 Full Stack)
- 4-stage approval flow adds significant n8n workflow complexity
- Character consistency architecture adds a layer Elbert didn't have
- 100 video/month scale requires queueing, error handling, retry logic
- Running costs are high enough that client must be financially capable to operate it

---

## Phase 2 Scope Interest (Music Video Editing)

Client described: provide footage angles, lighting, per-moment editing instructions, receive fully edited finished video. This is video editing automation, not AI generation. Possible with Creatomate templates but requires custom template architecture per music video type. Scoped separately after Phase 1.

---

## Client Behavior

- New to Fiverr
- Proposed $10-11/hr x 10hrs/day x ~20 days = ~$2,000 max (initial signal)
- Psychology: scared of being duped, not actually broke
- Fix: milestone payments (50/50) + proof of similar work + honest limitation disclosure
- Hold price. $3,500 fixed, not hourly.
- Once client sees the running cost math ($600-1,000/month), the build fee is obviously justified.

---

## Status

- Discovery questions: answered (2026-07-17)
- Response sent via Oba with $3,500 price + Phase 2 note
- Awaiting MadSoN's response to price
- No formal proposal document built yet

---

## Key Lesson

Same asset pricing principle as Elbert, but at a higher tier. A production studio capable of 100 videos/month cannot be priced at $2,000. The monthly running cost alone ($600-1,000) makes the build fee look small by month 3.

[[automation-asset-pricing]] [[elbert-savvysox]]
