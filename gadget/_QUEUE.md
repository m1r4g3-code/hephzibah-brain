---
sensitivity: private
entity_type: system
name: Gadget Priority Queue
last_updated: 2026-08-08
---

# Priority Queue — Gadget OS

Single source of truth for what needs to happen next in the gadget business, sorted by priority score.
Read by `scripts/heartbeat.py` at every session start. Update when items are created, resolved, or change state.

Priority score = `urgency_weight × revenue_multiplier × time_boost`

| Priority | Weight | Meaning |
|---|---|---|
| CRITICAL | 100 | Blocks revenue, cash at risk, or hard deadline <24h |
| HIGH | 70 | Time-sensitive, 24–72h window |
| MEDIUM | 40 | Important, this week |
| LOW | 10 | Backlog, no hard deadline |

Revenue multiplier: `DIRECT=1.5` (sells units) | `INDIRECT=1.0` (enables selling) | `MAINTENANCE=0.5` (keeps lights on)

Time boost: deadline today or past → ×2.0 · deadline tomorrow → ×1.5 · otherwise ×1.0

**Valid `state` values:** `open` · `in_progress` · `blocked` · `resolved` · `archived`
**Valid `category` values:** `sourcing` · `listing` · `pricing` · `content` · `supplier` · `order` · `cash` · `ops`

---

<!-- MACHINE-READABLE BLOCK — parsed by scripts/heartbeat.py. Keep it valid JSON. -->
```json
[
  {
    "id": "g005",
    "action": "Set up the Telegram bot — it is now the product intake, not just alerts",
    "context": "Promoted from LOW to CRITICAL on 2026-08-08. Emmanuel posts from his phone at Ikeja and is rarely at the machine, so the bot is the ONLY path for product photos and prices to reach the OS. intake.py is built and tested and does nothing without a token. Every other queue item is downstream of this one. NOTE: Telegram discards undelivered updates after ~24h, so also register the scheduled drain.",
    "priority": "CRITICAL",
    "revenue_impact": "DIRECT",
    "deadline": "2026-08-09",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "ops",
    "next_action": "BotFather → /newbot → token into config.py → python scripts/notify.py --get-chat-id → --test. Then python scripts/intake.py --install-task and run the printed command in an Admin PowerShell."
  },
  {
    "id": "g009",
    "action": "Content is the growth lever — demand is the binding constraint, not supply",
    "context": "Emmanuel moves 1-3 phones a week (confirmed 2026-08-08). Ikeja supply is effectively unlimited and he is not short of hours, so the business is short of BUYERS. Every gate and scorecard in this OS optimises a constraint he does not currently have. The qualification rubric is defence; content is offence, and right now the business is all defence. Highest-return activity available and nothing else is close.",
    "priority": "CRITICAL",
    "revenue_impact": "DIRECT",
    "deadline": "2026-08-15",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "content",
    "next_action": "Run /content-brief on the next phone that comes in. Start with the Buyer Protection angle — how to check a used iPhone before you pay. It builds the audience AND doubles as the sales pitch."
  },
  {
    "id": "g006",
    "action": "Ask Matte and Yemi the six vendor questions",
    "context": "Both supplier nodes exist but every commercial term in them is UNKNOWN. Under a broker model the vendor IS the inventory, so these six answers are worth more than any price list. One conversation each. Also establish the IMEI check as a universal routine NOW, while there is no problem — a check done on every unit is a policy, one done selectively is an accusation, and Matte is close enough personally that this will be awkward to introduce later.",
    "priority": "HIGH",
    "revenue_impact": "DIRECT",
    "deadline": "2026-08-12",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "supplier",
    "next_action": "Per vendor: (1) does a quoted price hold, how long? (2) will you hold a unit once my buyer commits? (3) how long? (4) what happens when a unit is bad? (5) can I inspect before money moves? (6) [Matte] your own stock vs your boss's — different terms? Write answers into the supplier nodes."
  },
  {
    "id": "g010",
    "action": "Decide the rule for deals where the vendor delivers direct",
    "context": "Emmanuel holds the phone on some deals and not others. The brand position is verified information — which cannot be claimed on a unit he has never touched. Publishing a spec as checked when it was not is the one failure that ends the business rather than costing money. Rule drafted in concepts/broker-model.md; needs his decision and then enforcement in the listing pipeline.",
    "priority": "HIGH",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-08-12",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "ops",
    "next_action": "Confirm the split rule: collected units get verified specs + photos; direct-delivery units get attributed claims only ('seller states 91%'). Then every pipeline row carries verified: true|false."
  },
  {
    "id": "g007",
    "action": "Calibrate the expected-spread bands from real deals",
    "context": "Emmanuel confirmed his cut scales with ticket size but did not give the numbers per tier. The bands in qualify.py (₦10k/₦15k/₦25k/₦40k) are inferred and currently flag a real ₦12k deal on a ₦435k phone as ₦13k short — which may be right, or may just be a wrong guess. Ten logged deals settles it. Hard floor stays ₦10k until then.",
    "priority": "MEDIUM",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-09-08",
    "owner": "Claude",
    "created": "2026-08-08",
    "state": "open",
    "category": "pricing",
    "next_action": "Log every deal with analytics.py --log-sale. At 10 deals, compare median spread per ticket band against BROKER_EXPECTED_BANDS and correct them."
  },
  {
    "id": "g001",
    "action": "Confirm identity/niche.md — is it phones-only or wider?",
    "context": "The OS ships with a researched default (phones, audio, power, wearables) inferred from me/identity.md. Everything Emmanuel has described so far is phones. Brand-fit is 15% of every score and reads from this file. Lower priority than it was — at 1-3 deals a week the niche file is not what is limiting the business.",
    "priority": "MEDIUM",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-08-15",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "ops",
    "next_action": "Confirm whether anything other than phones actually gets sold. If phones-only, cut the other categories from the IN table rather than leaving them aspirational."
  },
  {
    "id": "g002",
    "action": "Put real numbers in performance/metrics.md",
    "context": "Rewritten for the broker model on 2026-08-08. Available capital matters far less than first built — nothing is held — so the fields that matter now are deals per week, average spread, referral share, and channel mix. pulse.py reads this.",
    "priority": "MEDIUM",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-08-15",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "cash",
    "next_action": "Fill in: deals per week (1-3 confirmed), typical spread, WhatsApp/IG/X audience sizes. Capital fields can stay zero — no stock is held."
  },
  {
    "id": "g004",
    "action": "Backfill _PIPELINE.md with anything currently posted",
    "context": "Pipeline is empty. Any phone currently posted to WhatsApp status or IG is invisible to the OS. Under the broker model the risk this catches is the stale post — a live listing for a unit that has already sold from the group, which reads exactly like bait.",
    "priority": "MEDIUM",
    "revenue_impact": "DIRECT",
    "deadline": "2026-08-15",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "listing",
    "next_action": "List everything currently posted anywhere. One row per unit with model: broker, its vendor, and verified: true|false."
  },
  {
    "id": "g003",
    "action": "Create supplier nodes for every vendor in use",
    "context": "RESOLVED for the two known vendors. matte and yemi-group nodes created 2026-08-08. Two independent Ikeja sources on phones satisfies the supplier gate — while both stay live. Reopen if a third vendor appears.",
    "priority": "LOW",
    "revenue_impact": "INDIRECT",
    "deadline": null,
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "resolved",
    "category": "supplier",
    "next_action": "Done. matte + yemi-group nodes exist. Commercial terms still blank — that is g006."
  }
]
```

---

## Queue Discipline

1. **Every session end, resolve what got done.** Set `"state": "resolved"` and rewrite `next_action` to `"Done."` plus one line of what actually happened. Do not delete items — resolved items are the audit trail.
2. **Every new commitment becomes an item.** If Emmanuel says "I'll check that supplier tomorrow," it goes in the queue before the session ends. Spoken intentions that never reach the queue do not happen.
3. **Blocked items name the blocker.** `"state": "blocked"` requires the `context` field to say what is blocking and who can unblock it.
4. **IDs are sequential and never reused.** `g001`, `g002`, … Cross-domain items keep the same numeric suffix in both queues.
5. **The queue is capped at attention, not at count.** More than 8 open items means the queue is a wish list. Archive or resolve down to 8.
