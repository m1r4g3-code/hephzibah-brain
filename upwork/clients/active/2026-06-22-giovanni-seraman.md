---
sensitivity: private
entity_type: person
name: "Giovanni"
company: "SERAMAN"
platform: "Direct (email) — was Fiverr, banned 2026-07-24"
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

**Personal context:** In his 60s. No children. Patient, calm, kind man. Experienced businessman. Has partners he answers to ("I just have to keep my partners happy" — Jul 05) — not a solo decision-maker. Has been patiently working with Oba/Emmanuel for 1+ months, knows the pricing was low, still actively using the system. The relationship with Oba is warm and personal, not just transactional.

## Project: AI Video Production System

**Platform:** Was Fiverr (Oba's account — 50/50 split). Fiverr permanently suspended 2026-07-24 (TOS: AI video of public figures). Relationship maintained via direct email: seraman.adv@gmail.com. All future work is direct, no platform fee.
**Partnership:** Emmanuel built the entire pipeline solo. Oba managed client relationship and follow-up. Revenue split 50/50.
**Status:** BOTH milestones fully delivered and 5-starred BEFORE the Fiverr ban. Project is complete. Giovanni is now in ongoing relationship / next-phase pipeline.

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
| M1 + M2 combined | $1,000 total | Both delivered — both 5-starred before Fiverr ban |
| Long-form pipeline (5–8 min) | $3,000–$5,000 (market rate) | Not started — conversation to open |
| NGO project (partner) | $500+ for onboarding | Pending scope |
| Script preview gate (audio fix) | Small add-on if scoped separately | Being added |

**Note on financials:** Total project was $1,000 across both milestones. After Fiverr 20% fee → $800 → 50/50 with Oba → $400 each net. Market rate for what was built is $5,000–$8,000. Underpriced deliberately as a case study trade-off. The $1,500 floor mentioned in earlier notes was an internal Oba/Emmanuel agreement — not a price Giovanni accepted.

**Pricing note:** Never renegotiate closed delivered work. Future scope (long-form, NGO, retainer) to be priced at market rate with ROI framing. Giovanni's partners control his budget decisions — any price pitch must give him numbers he can show them.

## Review (Milestone 1)

> "Excellent work, fast and super professional. Perfect communication. They were able to produce what I asked for, modifying it as requested. Delivery was early. Highly recommended!!!"
> — Seller communication: 5 | Quality: 5 | Value: 5

## Flags

- **Green:** Pays, reviews promptly, clear feedback, expanding scope
- **Green:** Italian speaker — product content stays in Italian
- **Green:** Long-form project already scoped at $1,500
- **Watch:** Blotato posting failed once (execution 279, "Call Seraman Post to Socials") — social publishing still being confirmed

## M2 Testing — Bugs Found (2026-06-28)

Two test videos run: Gatorz Magnum OPz sunglasses + CVN4 Tactical Responder Bandage.

**Confirmed bugs (all root-caused):**

1. **English caption "That changes everything" (sunglasses video, frame 4)**
   Root cause: n8n Edit Videos Code node maps `video_prompt` (English) to Creatomate caption field instead of `voiceover_text` (Italian).
   Fix: Change caption field source in Edit Videos Code node to `voiceover_text`.

2. **Doubled/garbled captions (sunglasses video, frame 9)**
   Root cause: Creatomate template has a second text element also receiving voiceover_text.
   Fix: Delete second text element in Creatomate template editor.

3. **"s bliped" hallucinated background text (sunglasses video, frame 9)**
   Root cause: Kie AI reads blurry store shelf packaging and completes partial text. "no text overlays" doesn't cover environmental surfaces.
   Fix: Add full environment text block to every presenter scene prompt. See [[kie-ai-veo3-prompt-engineering]].

4. **Hallucinated label on CVN4 package (CVN4 video, frames 1-2, 15-16)**
   Root cause: Product name "CVN4 Tactical Responder Bandage" in opening dialogue declaration → Kie AI renders it as a printed label on the packaging surface.
   Fix: Don't open dialogue with product name as standalone declaration. Move name mid-sentence. Put no-text block at START of prompt.

5. **Skull and crossbones on CVN4 (CVN4 video, frame 7) — HARD BLOCKER**
   Root cause: TCCC + "no second chance" language triggers Kie AI danger symbol association.
   Fix: Add `no skulls no crossbones no danger symbols no hazard markings` to no-text block. Put block at top of prompt.

6. **Wrong product form (CVN4 video, frame 9)**
   Root cause: CVN4 prompts alternate between vacuum package and unrolled bandage across scenes, but only one product image URL is passed to all scenes. Kie AI generates inconsistent product representations.
   Fix: Either (a) pick one product form for the whole video, or (b) support per-scene product images in the pipeline schema.

**System prompt fix needed (v5.1 → v5.2):**
- No-text rules block must be FIRST in prompt, before camera and dialogue
- Dialogue must not open with product name as standalone declaration
- Remove Think tool from LangChain agent (incompatible with Structured Output Parser)

**Strategy:** Include scene-level approval + selective regen system in M2 delivery (not as paid M3). Rebuilds trust after these QC issues. Long-form ($1,500) pitched as clean M3 from restored trust position.

## Client Feedback Log

### Giovanni, Jul 06 2026 3:12 PM (verbatim, on the sunglasses M2 test video)

> Good job! We're almost there, I just need to fix the text because the pronunciation on some things isn't correct. But this is a problem with all AIs that read in one language and don't change their accent when they read a word in another. For example, "cerakote" is English, and it reads it in Italian as it's written. In this case, just write the word "ceracot" and it's in English. Just write the correct text and you're done. A few things:
> - the glasses in the last scene aren't the ones shown;
> - there are some sharp cuts between one scene and the next; something would be needed to translate them;
> - the volume is generally low, but that's secondary for now.
> - the writing in the bottom right is "seraman," too "bare."
> But let's just say we're getting down to the details; generally speaking, we're on the right version.
> Bravo

**Status check against current pipeline (as of 2026-07-10):**

1. **Pronunciation of English loanwords read in Italian accent** ("cerakote" → should be spelled phonetically, e.g. "cerakot", so Italian TTS doesn't read it letter-for-letter) — **FIXED, script agent v5.10 (2026-07-10).** Added a mandatory phonetic-respelling rule for English brand/technical terms inside spoken VO ("Cerakote" → "Cerakot" pattern), with a new pre-output checklist item. Live on n8n node "SERAMAN | Generate Script" (workflow `bIDbAPsBbK9wh0c6`), published `activeVersionId: a976a2a5-563a-44ec-9eab-981712aa656b`, byte-verified against source.
2. **Wrong glasses/product shown in last scene (scene 8)** — **RE-CHECKED, ALREADY FIXED.** Inspected the live "SERAMAN Generate Images" workflow (`R2uqd2tnN687vcuH`, updated 2026-07-08 — after Giovanni's message): the Kie submit node sources `PRODUCT IMAGE` / `PRODUCT IMAGE 2` identically for every scene including scene 8, no divergent path. This was likely already broken when Giovanni saw it (Jul 06) and got fixed by the time this workflow was last touched. A separate, narrower bug remains on the hardening list — scene 1/8's *video regen* path (only triggers if those scenes get flagged for regen) still uses an older generation mode — but that's not what caused the original wrong-product complaint.

**Bonus fix while applying v5.10 (2026-07-10):** Publishing the script agent workflow re-surfaced a known recurring n8n bug (see [[n8n-mcp-gotchas]]) — two Gmail alert nodes, "SERAMAN | Reject Invalid Input" and "SERAMAN | Duplicate Submission Alert", had their `operation` parameter wiped (missing "send"), meaning those client-facing rejection/duplicate emails likely weren't sending. Pre-existed my changes (same warning showed up before I touched anything), not caused by this session — but fixed and published now.
3. **"Sharp cuts between scenes... something would be needed to translate them"** — re-read (2026-07-10, operator's call): "translate" is almost certainly a mistranslation of "transition," but the real cause is probably not a missing visual effect — it's the presenter's VO not finishing before the hard 8-second scene cut, which reads as an abrupt/incomplete cut regardless of any crossfade. **LIKELY FIXED, NOT RECONFIRMED ON THIS EXACT VIDEO.** This matches the "speech cut mid-sentence at every 8s boundary" bug fixed via script agent v5.6 (12-word VO cap, 15 for scene 2, "finish by second six" pacing), whisper-verified on a later job at 6.2–7.5s speech-end out of 8s. Giovanni's message (Jul 06 3:12 PM) falls right in the window of that fix — plausible his feedback is what triggered it — but there's no confirmation the fix had landed on the specific render he was reacting to. (Separately, every scene does also have a 3.5s fade-in animation live in the current Creatomate template, so the visual-transition reading, if that's what he meant, is also covered.)
4. **Volume generally low** — **MOSTLY FIXED.** Scenes 2–7 audio boosted to 200% volume (done in an earlier session — "edit the json template for each scene to be 200% not 100% for scene 2-7"). Scene 1 is still at 60% and scene 8 has no volume override (defaults to 100%) — worth normalizing these two to match the rest.
5. **"seraman" bottom-right end-card text too bare** — **UNCONFIRMED, LIKELY STILL OPEN.** The only branded text/logo element in the render is the outro CTA ("Shop now at: seraman.com" + logo image) at the very end of the video — plain Montserrat white text with a thin dark stroke, no visual upgrade evident since Jul 06. Would need an actual rendered video to confirm whether this reads as "bare" now.

## M2 Breakthrough — Pipeline Proven End-to-End (2026-07-05 → 06)

First-ever complete run: form approval → script → 8 images → 8 Veo videos → Creatomate edit → client review email. Then the scene-regen loop ran for the first time and was proven live: Giovanni-side flag (scenes 2–7) → regen with corrected prompts → re-edit → branded re-review email. Total spend for the regen round: 6 Kie credits, zero waste (the one failed attempt cost nothing — Kie only bills successful generations).

**Bugs found and fixed live (all in production now):**
1. Italian VO coin-flipping to English — `enableTranslation: true` on Kie submits translated quoted dialogue; set false on all dialogue-scene submit nodes (3 places).
2. Speech cut mid-sentence at every 8s scene cut — script agent wrote ~20-word VO lines needing ~10s; hard cap now 12 words (15 for scene 2) + "finish by second six" beats (system prompt v5.6).
3. Regen branch dead on arrival — prompt-cleaning agent nested output under `output`, downstream read top-level → empty prompts to Kie (422). Fixed with flatten node.
4. "Increment Regen Round" wrote to a nonexistent Sheet3 column → chain silently stopped; column added.
5. Regen retry counter reset every cycle → infinite 3-min poll loop on permanent failure; now carried through the wait loop.
6. Creatomate API key invalid (401) — Giovanni-side credential refresh.

**Also shipped:** all 9 client-facing emails re-skinned with the branded dark Seraman template (status badges, buttons, logo chip); rejection email rewritten from a bare "incomplete details" stub.

**Verification method worth reusing:** downloaded the final render, split audio per 8s scene with ffmpeg, transcribed each with faster-whisper (language detection per scene) — caught the English scene and measured speech-end times (7.6–8.0s before fix, 6.2–7.5s after) without burning a single credit on guesswork.

**Remaining before full M2 sign-off:** Post-to-Socials stage (Blotato) still never run — fires on Giovanni's approve; scene 1/8 regen path uses old generation mode (align with proven branch A); Sheet2 stale duplicate rows corrupt regen URL writes (dedupe); idempotency guard so crashes never re-burn credits; script-agent prompt slimming. Big-product caveat for future jobs: concept assumes handheld items — large gear (cots, tents) needs a "large item" presenter mode; the image-approval gate is the cheap test.

## Incident — Kie Outage on Real Client Job + Image Quality Bugs (2026-07-08 → 09)

**Real job PRB1RG5 (rangefinder "Impact 4000") hit a live Kie platform outage.** All 8 scenes failed video generation, Edit Videos threw "Cannot render final video - bad scene URLs" (execution 545), and the Error Handler sent Giovanni a plain **"[FAILED] Seraman Edit Videos"** email (execution 546, 2026-07-08 23:35 UTC) — generic red failure badge, no indication it was Kie's outage and not our workflow. Unknown whether Giovanni saw/reacted to this specific email before the fix below shipped — worth confirming with him directly.

**Fix shipped:** Error Handler email template now distinguishes Kie-platform-caused failures (amber, "upstream provider issue") from actual workflow bugs (red) so Giovanni never mistakes a Kie outage for broken automation.

**Separately, image-generation quality bugs surfaced from screenshot QC (job aODBMQE, CVN4 Trauma Responder Bandage):**
1. **Subject missing in some scenes** — investigated, found mostly intentional (Scene 5's hands-only macro is a deliberate grip-demo per the script agent's Feature-to-Visual Mapping), not a systemic bug. Rule tightened in v5.8 so this stays a rare, justified exception.
2. **Product scale inconsistent / rendered too large** (bandage) — genuine architecture gap: no scale-anchor language ever existed in the prompt spec. Root-caused and fixed in script agent **v5.8** (scale classification + anchor phrasing bank, mandatory presenter face-in-frame). First regen of scenes 2 & 7 for aODBMQE **did not visually fix it** — caught directly by comparing before/after screenshots. Root cause of that: the scale-anchor sentence was appended after a handling action ("holds it flat between both open palms") that itself implied a two-handed span — nano-banana-pro follows the described physical motion over a trailing descriptive sentence. Fixed properly in **v5.9**: rewrote the handling action itself to a one-hand cupped-palm motion, hardened the prompt with an explicit rule forbidding a scale clause that contradicts the action verb. Both scenes regenerated and re-sent to seraman.adv@gmail.com.

**Script agent is now on v5.9** (live in n8n node "SERAMAN | Generate Script", workflow bIDbAPsBbK9wh0c6), byte-verified.

## Ad Creative — Video Model A/B Test (2026-07-19)

Veo3 has a recurring shape-drift defect on hand/joint contact scenes (observed on Disk-Bunk job WJpQ9eR, scene 7 — presenter hand seating a pole into a disc adapter). Ran a real, controlled test: same reference images, same prompt, same scene, submitted to 3 alternative Kie AI models to see if any fix it natively.

**Result (verified frame-by-frame, t=1/3/5/6.5s, not just spec claims):**
- **Kling 3.0** — fixes the joint defect. Voiceover reads robotic/synthetic.
- **Seedance 2.0** — introduces a new, different defect (phantom object duplication). Also by far the most expensive. Disqualified.
- **Gemini Omni** (Google's own model, via Kie) — fixes the joint defect. Voiceover reads natural/human. Fastest generation of the three. **Best pick.**

**Verified per-clip cost (from actual `creditsConsumed`, not published estimates):**
| Model | Cost/8s clip |
|---|---|
| Veo3 Fast (current) | $0.30–$0.40 |
| Gemini Omni | $0.525 |
| Kling 3.0 | $1.08 |
| Seedance 2.0 | $4.08 |

**Status:** 4-way comparison video sent to Giovanni with cost breakdown and recommendation to switch to Gemini Omni (cheaper than Kling, fixes the defect, better VO). Awaiting his greenlight. If approved, production workflow `fygNTt3a5LphUJO7` ("Seraman Generate Videos") needs its Kie submit nodes pointed at `gemini-omni-video`. Only tested against this one defect class — character consistency across a full 8-scene job and material hallucination not yet stress-tested on Omni.

## Ad Creative — Background Music Research (2026-07-20)

Investigated whether to replace the current stock background track. Key findings:

- **Do not use live trending TikTok/Reels sounds.** They're licensed for organic posts, not paid ad placement, and burn out in 1–2 weeks — wrong fit for a Creatomate-rendered ad meant to run for a while.
- Commercial-library tracks in the **100–140 BPM** range consistently outperform generic background music for this content type.
- Pairing music with voiceover (already the Seraman format) gets roughly **2x the conversion** of either alone per TikTok ad data — don't let music compete with/drown the VO.
- One concretely documented reference: Artlist track **"Game Over" by 2050** — electronic + orchestral, builds from dramatic strings/synths into driving percussion and brass. Picked by an automotive brand for a cinematic commercial. Closest verified match to the rugged/confident/builds-to-a-payoff register Seraman needs. Worth previewing directly on Artlist.
- **Real validation method (not yet run):** check Meta Ad Library (facebook.com/ads/library) for live video ads from comparable DTC tactical/EDC brands — Tactical Geek, 5.11 Tactical, Elite Survival Systems, Marsupial Gear, M-Tac, Falco. A track reused across multiple currently-running ads from different advertisers is real proof it converts (they're paying to keep it live).

**Status:** research only, no track selected yet. Next step is the Meta Ad Library check above before locking a replacement track.

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

---

## Session Log — 2026-07-28/29

### Fiverr Ban Impact
Oba's Fiverr account permanently suspended 2026-07-24 (TOS: AI video of public figures). Giovanni was not lost — relationship maintained because his email was on file. Direct email channel is now the only contact method. No platform fee going forward.

### Giovanni Email — 2026-07-28 21:10
Giovanni emailed Oba/Adelaja directly at seraman.adv@gmail.com with two issues on the water-purifying tablets video:

1. **Audio editing request:** "I need to figure out how to edit the audio text directly after the video is generated, if possible." — He wants to catch wrong pronunciations/lines before final render. VO is baked into Kie clips and cannot be edited post-generation. Fix: add a script preview/approval gate so he sees and edits the script BEFORE Kie runs. Being added as a feature.

2. **Pill packaging display errors:** "In the various clips, there are many errors in the display of the pill packaging. The only real one is the one you see at the end of the video." — Classic Kie AI product hallucination across scenes. Earlier clips showing wrong/inconsistent packaging. Fix: isolate affected scenes, regenerate with cleaner product image references and tighter prompt constraints. Same root cause as CVN4 packaging bug (see M2 bugs section).

He also said: "The audio is almost perfect" — positive signal. Still actively using the system on new products post-ban.

### Honest Ask — 2026-07-29
After the pipeline went cold on all other fronts (Elbert ghosted, Petit Lit no reply, DesignRush no conversions, Bayonet demo-blocking), Giovanni is the only warm relationship active.

Oba sent Giovanni a direct honest ask (2026-07-29) — not manipulation, not guilt. Acknowledged the $1,000 was their own call, mentioned the AI tools need renewing, gave him a clean exit ("nothing changes between us if the answer's no"). Also mentioned the script preview gate fix being added as a goodwill gesture.

Final message sent by Oba:
> "We built the SERAMAN pipeline at $1,000, we know that was below what the work was worth. That was our call, we wanted the project and the case study, and we stand by it. We're also adding a fix on our end so you can catch a wrong line in the script before the video's even generated, should mean you never need a full remake again. Separately: we're at the point where we need to renew the AI tools behind the fast builds. Not asking to revisit what's already paid, just being straight with you. If you've been happy with the work and want to see it keep improving, any contribution toward that would go a long way. No pressure either way, nothing changes between us if the answer's no."

Awaiting Giovanni's reply.

### Next Pipeline (Priority Order)
1. **Honest ask response** — await Giovanni's reply, no follow-up pressure
2. **Long-form video package** — $3,000–$5,000. Open this conversation after honest ask resolves. Use ROI framing for his partners.
3. **NGO onboarding** — Giovanni's partner runs an NGO project on the pipeline. Scope as a separate paid contract (~$500+). Not free support.
4. **Script preview gate** — build the approval step so Giovanni sees and edits script before Kie runs. Solves the audio editing request permanently.
5. **Gemini Omni switch** — awaiting Giovanni's greenlight on the model comparison (q008). Follow up if no reply.
6. **Volume fix** — Scene 1 (60%) and Scene 8 (100%) need to be normalized to 200% to match scenes 2–7 (q007).

### Relationship Intelligence
- Warm, personal, patient relationship — primarily via Oba
- Giovanni is not a solo decision-maker — his partners control budget approvals
- He knows the price was low — has never weaponized this
- No children — has shown genuine interest in the work, not just transactional
- Most likely to respond positively to honest, direct communication — not sales framing
- Any price pitch for future work must include ROI numbers he can show his partners
