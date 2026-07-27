---
sensitivity: private
entity_type: system
name: Priority Queue
last_updated: 2026-07-27
---

# Priority Queue — Upwork OS

Single source of truth for what needs to happen next, sorted by priority score.
Read by `scripts/heartbeat.py` at every session start.
Update when items are created, resolved, or change state.

Priority score = urgency_weight × revenue_multiplier
- CRITICAL = 100 (blocks revenue / hard deadline <24h)
- HIGH     = 70  (time-sensitive, 24-72h window)
- MEDIUM   = 40  (important, this week)
- LOW      = 10  (backlog, no hard deadline)

Revenue multiplier: DIRECT=1.5 | INDIRECT=1.0 | MAINTENANCE=0.5

---

<!-- MACHINE-READABLE BLOCK — parsed by scripts/heartbeat.py -->
```json
[
  {
    "id": "q001",
    "action": "Resolve Upwork account restriction",
    "context": "Trust & Safety flag. Support ticket submitted. Watch adekoyaemmanuel15@gmail.com for response. Blocking all bidding and connect purchases.",
    "priority": "CRITICAL",
    "revenue_impact": "DIRECT",
    "deadline": "2026-07-29",
    "owner": "Emmanuel",
    "created": "2026-07-27",
    "state": "open",
    "platform": "Upwork",
    "next_action": "Check email for Upwork support reply. If no reply by 2026-07-29, follow up via support ticket."
  },
  {
    "id": "q002",
    "action": "Chase Bayonet — payment number + logo PNG",
    "context": "Revamp Consulting build is blocked. Bayonet confirmed the project but hasn't sent payment WhatsApp number or logo file. No number = no invoice. No logo = no build.",
    "priority": "HIGH",
    "revenue_impact": "DIRECT",
    "deadline": "2026-07-28",
    "owner": "Emmanuel",
    "created": "2026-07-24",
    "state": "open",
    "platform": "Direct",
    "next_action": "WhatsApp Bayonet: 'Hey, just need your payment number and the logo PNG to kick off the build.'"
  },
  {
    "id": "q003",
    "action": "Follow up Petit Lit (Fradel Saks) if no reply",
    "context": "Reconnect email sent 2026-07-24 to sales@petitlitfurniture.com. If no reply by 2026-07-27, call 718.851.0367.",
    "priority": "HIGH",
    "revenue_impact": "DIRECT",
    "deadline": "2026-07-27",
    "owner": "Emmanuel",
    "created": "2026-07-24",
    "state": "open",
    "platform": "Direct",
    "next_action": "No email reply yet. Call 718.851.0367 or send follow-up email."
  },
  {
    "id": "q004",
    "action": "LinkedIn Post 3 — publish 8AM WAT",
    "context": "Hard schedule. Post 1: 2026-07-24 done. Post 2: 2026-07-26 done. Post 3: 2026-07-29. Must be online 60 min after posting. First comment within 60 seconds.",
    "priority": "HIGH",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-07-29",
    "owner": "Emmanuel",
    "created": "2026-07-24",
    "state": "open",
    "platform": "LinkedIn",
    "next_action": "Prepare Post 3 content and card before 2026-07-29 8AM WAT."
  },
  {
    "id": "q005",
    "action": "Giovanni NGO project — scope the onboarding",
    "context": "Giovanni's partner is managing the NGO project. Pipeline probe sent. Partner onboarding is a paid deliverable — do not give it away as free support. Awaiting Giovanni's reply on what product they're running.",
    "priority": "HIGH",
    "revenue_impact": "DIRECT",
    "deadline": "2026-07-30",
    "owner": "Oba",
    "created": "2026-07-27",
    "state": "open",
    "platform": "Direct",
    "next_action": "Await Giovanni's reply. When he confirms product, scope the onboarding as part of NGO contract."
  },
  {
    "id": "q006",
    "action": "Gadget/phone sales OS — design and build",
    "context": "Emmanuel runs a gadget/phone sales operation. Needs: brand system, daily photo posting engine, posting strategy, n8n automation for cross-posting. 5 clarifying questions pending answers.",
    "priority": "MEDIUM",
    "revenue_impact": "INDIRECT",
    "deadline": null,
    "owner": "Emmanuel",
    "created": "2026-07-27",
    "state": "open",
    "platform": "Direct",
    "next_action": "Emmanuel to answer: (1) new/used/both stock, (2) brand name exists?, (3) units/week, (4) WhatsApp Business set up?, (5) current photo setup."
  },
  {
    "id": "q007",
    "action": "SERAMAN — normalize scene 1/8 volume to 200%",
    "context": "Scene 1 at 60%, scene 8 at 100%. Scenes 2-7 at 200%. Inconsistent. Giovanni flagged volume before. Low priority but should be fixed before next M2 job.",
    "priority": "MEDIUM",
    "revenue_impact": "MAINTENANCE",
    "deadline": null,
    "owner": "Emmanuel",
    "created": "2026-07-24",
    "state": "open",
    "platform": "n8n",
    "next_action": "Update Creatomate template for scene 1 and scene 8 volume to 200%."
  },
  {
    "id": "q008",
    "action": "SERAMAN — Gemini Omni switch pending Giovanni greenlight",
    "context": "A/B test run 2026-07-19. Gemini Omni fixes hand/joint defect, better VO, cheaper than Kling. 4-way comparison sent to Giovanni. Awaiting his approval to switch production workflow.",
    "priority": "MEDIUM",
    "revenue_impact": "MAINTENANCE",
    "deadline": null,
    "owner": "Oba",
    "created": "2026-07-19",
    "state": "open",
    "platform": "n8n",
    "next_action": "Follow up with Giovanni if no reply on the model comparison email."
  },
  {
    "id": "q009",
    "action": "OS Tier 2 — Priority Queue + Heartbeat built",
    "context": "Architectural improvements to move OS from reactive shell to intelligent event-driven system. In progress this session.",
    "priority": "MEDIUM",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-07-27",
    "owner": "Emmanuel",
    "created": "2026-07-27",
    "state": "in_progress",
    "platform": "OS",
    "next_action": "Complete build: state machine, event catalog, heartbeat.py, pulse.py, CLAUDE.md updates."
  }
]
```
<!-- END MACHINE-READABLE BLOCK -->

---

## Current Queue — Human View

| Priority | ID | Action | Owner | Deadline | State |
|---|---|---|---|---|---|
| 🔴 CRITICAL | q001 | Resolve Upwork account restriction | Emmanuel | 2026-07-29 | open |
| 🟠 HIGH | q002 | Chase Bayonet — payment + logo | Emmanuel | 2026-07-28 | open |
| 🟠 HIGH | q003 | Petit Lit follow-up if no reply | Emmanuel | 2026-07-27 | open |
| 🟠 HIGH | q004 | LinkedIn Post 3 — 8AM WAT | Emmanuel | 2026-07-29 | open |
| 🟠 HIGH | q005 | Giovanni NGO — scope onboarding | Oba | 2026-07-30 | open |
| 🟡 MEDIUM | q006 | Gadget OS design | Emmanuel | — | open |
| 🟡 MEDIUM | q007 | SERAMAN scene 1/8 volume fix | Emmanuel | — | open |
| 🟡 MEDIUM | q008 | SERAMAN Gemini Omni greenlight | Oba | — | open |
| 🟡 MEDIUM | q009 | OS Tier 2 build | Emmanuel | 2026-07-27 | in_progress |

---

## How to Maintain This File

- Add items: append to JSON block + add row to table
- Resolve items: change `"state": "open"` → `"state": "resolved"`, remove from table
- Escalate items: change priority level when deadline pressure increases
- heartbeat.py reads the JSON block automatically — keep it valid JSON
