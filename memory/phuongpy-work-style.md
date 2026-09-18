---
name: phuongpy-work-style
description: "Phượng's real work style, decision patterns, and technical capability — derived from her own Slack self-DM weekly notes and team threads, not from documents about her"
metadata: 
  node_type: memory
  type: user
  originSessionId: 12a24032-5a00-438d-86c3-d8ba57dc88a0
  modified: 2026-09-14T11:08:51.165Z
---

**Identity**: Phạm Yến Phượng (Slack `phuongpy`, `yenphuong.pham.work@gmail.com`), Digital Marketing at Teeinblue. GitHub: `yenphuongphamwork`.

**Brainstorm style she wants** (her own choice, not assumed): a mix of — challenge weak assumptions directly, lay out multiple options with trade-offs, and ask clarifying questions before proposing. Not "just give one strong recommendation."

**Autonomy she wants**: case-by-case — small/low-risk tasks can be done and shown after; bigger or ambiguous-direction tasks should be checked first. No fixed rule; use judgment on risk/reversibility.

**What frustrated her about AI tools before**: generic advice not grounded in Teeinblue's actual context, fabricated stats/info, wrong tone/voice. → Never invent a number; always ground in the real knowledge base/Confluence/data; match brand voice exactly (see [[teeinblue-content-team-playbook]]).

**Technical capability (from her own account in a team AI-reflection thread, Aug 2026):**
- She codes **frontend** for Shopify-theme pages herself using AI (e.g. AI Prompt Library page) — only needs a dev (usually "Phát") for **backend logic**.
- She runs **database/Grafana queries herself via AI** once a dev has written the query — but if a query needs to be written from scratch, she still needs dev help because the business definitions are "messy and undocumented enough that AI can't read them reliably." → When she asks for a new metric never queried before, don't assume `gq` can just produce it — check `knowledge/07-terms.md` for ⬜ (unconfirmed) terms first.
- She personally maintains an extremely detailed, rigorous data-verification log for the market report pipeline (`TIB-Grafana-Query/MARKET_REPORT_STATUS.md`, ~1900 lines) — cataloging every data trap found (bad `usages` rows, JSON format changes mid-period, DB-load timing effects, chunk-size tuning, a Windows encoding bug). She thinks about data correctness at a very rigorous level (e.g. rejected a dev's query because it silently undercounted by measuring post-order state instead of add-to-cart).

**Decision-making pattern observed** (e.g. infographic-seeding call, Sept 2026): raises a strategic trade-off explicitly to the team before committing (e.g. "will seeding the full infographic cannibalize report downloads?") rather than deciding alone when it affects shared strategy. Iterates fast on concrete feedback (color-coding rules, missing elements) and reships within minutes — not defensive about being corrected.

**Full range of task types she's handled month-to-month** (see [[teeinblue-marketing-team]] for the team-context version) — this is NOT static; new landing pages/campaigns rotate in every 1-2 months. Recurring core: newsletter (weekly), Shopify Community seeding, monthly report+plan. Recent project cycles: pricing rollout comms → Hire a Partner/Expert page → Image Enhancer/BG Remover free tools → AI Prompt Library → market report (full data→design→promote cycle). Constant thread: FB/Etsy ads hands-on management (day-by-day banner/audience testing, logged manually) and competitor monitoring (Easify, Customily, Customix) done by her own initiative, not assigned.

**Existing personal automation — check [[teeinblue-automation-inventory]] before ever proposing to build something for her.** She has already built and is running: a Grafana query CLI, a scheduled Shopify-Community-thread scanner, a full newsletter pipeline, and an expert-directory-page updater. Proposing to "build" one of these from scratch (as happened once in this project) is a real failure mode — always check the inventory file first.

## Update protocol for this file
Edit in place when a fact changes (don't just append) — e.g. if her autonomy preference or brainstorm style shifts. If a correction reverses something previously written, leave a one-line `_Corrected <date>: was "..." — now "..."_` note so a future read doesn't get confused by stale phrasing elsewhere in this file.
