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
    "id": "g001",
    "action": "Fill identity/niche.md with the real category list",
    "context": "The OS ships with a researched default (phones, audio, power, wearables) inferred from me/identity.md. Emmanuel and Yemi need to confirm or correct it. Every qualify.py score depends on brand-fit weighting, which reads from this file. Wrong niche file = wrong scores on every product from here on.",
    "priority": "HIGH",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-08-11",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "ops",
    "next_action": "Open gadget/identity/niche.md. Confirm or edit the IN and OUT category tables. Commit."
  },
  {
    "id": "g002",
    "action": "Set real numbers in performance/metrics.md",
    "context": "Metrics file ships with a zeroed baseline. Cash available, current stock value, and last 30d units are all unknown to the OS. pulse.py and every pricing decision read from here. An OS operating on zeros will recommend stocking things the business cannot fund.",
    "priority": "HIGH",
    "revenue_impact": "DIRECT",
    "deadline": "2026-08-11",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "cash",
    "next_action": "Count actual stock on hand and available buying capital. Write both into gadget/performance/metrics.md. Run python scripts/pulse.py to confirm it reads."
  },
  {
    "id": "g003",
    "action": "Create supplier nodes for every vendor currently in use",
    "context": "Supplier gate says never sole-source a top-5 product. The OS cannot enforce that with zero supplier nodes. Every Computer Village vendor, every importer, every contact Yemi buys from needs a node with lead time, MOQ, and payment terms.",
    "priority": "MEDIUM",
    "revenue_impact": "INDIRECT",
    "deadline": "2026-08-15",
    "owner": "Emmanuel + Yemi",
    "created": "2026-08-08",
    "state": "open",
    "category": "supplier",
    "next_action": "For each existing vendor run /supplier-intel [name]. Minimum three nodes before the supplier gate has anything to check against."
  },
  {
    "id": "g004",
    "action": "Backfill _PIPELINE.md with products already being sold",
    "context": "Pipeline is empty at build time. Anything currently in stock or already listed is invisible to heartbeat.py, so stale-stage detection (sourcing >14d, approved-not-published >7d) has nothing to fire on.",
    "priority": "MEDIUM",
    "revenue_impact": "DIRECT",
    "deadline": "2026-08-15",
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "sourcing",
    "next_action": "List everything currently held or listed. Add one row per SKU to gadget/_PIPELINE.md with its real stage_entered date."
  },
  {
    "id": "g005",
    "action": "Configure Telegram bot for gadget alerts",
    "context": "notify.py is built and working but has no token. Without it there is no push channel for price alerts, low-stock warnings, or supplier decisions — everything stays trapped in the terminal.",
    "priority": "LOW",
    "revenue_impact": "MAINTENANCE",
    "deadline": null,
    "owner": "Emmanuel",
    "created": "2026-08-08",
    "state": "open",
    "category": "ops",
    "next_action": "BotFather → /newbot → put token in config.py → python scripts/notify.py --get-chat-id → python scripts/notify.py --test"
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
