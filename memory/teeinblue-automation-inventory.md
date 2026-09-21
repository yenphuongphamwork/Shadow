---
name: teeinblue-automation-inventory
description: "Inventory of automation/tools Phượng (or the team) has already built — check this BEFORE proposing to build anything, so the agent doesn't suggest rebuilding something that already exists"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 12a24032-5a00-438d-86c3-d8ba57dc88a0
  modified: 2026-09-21T08:14:15.313Z
---

Found by reading her local `~/github/` repos + Slack (14/09/2026). **Read this before proposing any new automation** — a past mistake in this project was proposing to build a Shopify-Community seeding tool and a market-report data pipeline that both already existed and were mature.

## Her personal repos (local at `~/github/`, GitHub `yenphuongphamwork`, private)

- **`TIB-Grafana-Query`** (`gq`) — CLI to run SQL on Grafana (`metric.teeinblue.com`) from terminal via the HTTP API, no browser needed. Not just a raw query tool: has 7 purpose-built scripts — `run_range.py` (monthly value), `run_funnel.py`/`run_funnel_year.py` (add-to-cart/checkout by feature), `run_features.py` (campaigns by feature), `run_top_products.py`, `run_ai_images.py`, `run_sql_months.py` (generic monthly runner). `MARKET_REPORT_STATUS.md` in this repo (~1900 lines) is her running verification log for the market-report data pipeline — full of hard-won data traps (see [[phuongpy-work-style]]). **This repo is effectively the market-report data pipeline already** — don't propose building one.
- **`TIB-Expert-Page-Updater`** — reads a new row from the "Teeinblue Expert Information" Google Form/Sheet (OAuth, as her), downloads the applicant's images from their Drive, formats to the Shopify theme's schema, uploads images, appends a new expert block to the Hire an Expert page. Always previews before writing.
- **`TIB-Newsletter-Photo-Uploader`** — near-fully-automated Teeinblue Insider newsletter pipeline run from Claude Code: processes images → uploads to Shopify Files → builds HTML from Brevo template #27 → creates/updates the Brevo draft → sends her a test email. Deliberately **stops after the test send** — real subscriber lists are never auto-sent to. She does final review + schedule herself in Brevo.
- **`TIB-Shopify-Community-Thread-Scan`** — scans Shopify Community for seeding-relevant threads (`scan.py`); **actually running on a schedule** via a registered `launchd` job (`teeinblue.shopifycommunityscanner`, Mon+Thu mornings). Setup/workflow documented on Confluence: "Seeding Shopify Community Automation" (space TM). This already solves "seeding automation" — don't re-propose it.
- **`TIB-GA4-Query`** (`ga4.py`) — terminal GA4 Data API reports (channels/sources/pages/events/custom), OAuth read-only "as her", token auto-refresh (headless-capable after first consent). For the **Website / Blog / AI-search** report sections (traffic, source/medium, install-button & register clicks, top pages, countries). Scaffolded 2026-09-21 (Opus), **syntax-checked but NOT run end-to-end yet** — needs her one-time setup: chị Trang grants her Google account Viewer on the GA4 property, she enables the Analytics Data API + makes an OAuth desktop client (`client_secret.json`), fills `config.json` property_id. Local repo committed; GitHub remote not created yet (no gh CLI → she makes the empty private repo, then push). **Does NOT have App Store installs** (that's Shopify Partner). Don't use `gq` for installs.

## Team-level repo

- **`blog-automation`** (`github.com/ownego/blog-automation`, shared, mainly used by Hạnh/Thảo) — Claude-Code-driven pipeline: keyword brief → outline → draft → review → Confluence page → images → publish to Shopify (as hidden draft, human saves). Also has an `/optimize` mode to refresh an existing published post. Logic lives in `CLAUDE.md`/`OPTIMIZE.md` in that repo. This is the "Claude code → optimize blog creation flow" referenced in the Sept 2026 action plan.

## Templates/trackers on Google Drive (not code, but reusable — check before recreating)

- **"TIB Data Request For Market Report.xlsx"** (shared, owned by contact@teeinblue.com) — the standing data-request template for each report cycle; she doesn't write the spec from scratch each time.
- **"TIB - Report Table Hx/20xx"** (Google Sheet, shared by contact@teeinblue.com) — the monthly team report-numbers tracker ktrang asks everyone to fill in.
- **"Teeinblue Expert Information (Responses)"** — the Google Form response sheet that feeds `TIB-Expert-Page-Updater`.
- Page-content docs she authored directly on Drive: "Hire An Expert Page Structure & Content", "Become a partner page structure", "FAQs Image tools" — read these for her actual shipped copy/voice before drafting anything similar rather than starting blank.

## Genuine remaining gaps (as of 14/09/2026 — verify with her before assuming still true)

1. **Ads performance (FB/Etsy)** — no repo/tool found; she appears to still log day-by-day test results manually in her self-DM.
2. **Competitor snapshot** — no repo/tool found; she notes competitor moves (Easify, Customily, Customix) manually when she notices them.
3. **App Store installs/ranking (Shopify Partner)** — still no tool/connector (Partner dashboard has no API here; the registry's Shopify connector is store-level, not Partner). Website traffic/conversion side is now covered by `TIB-GA4-Query` (once set up); App-Store-install side still comes from the monthly "TIB - Report Table" sheet + #tib-mkt-alert.

## Update protocol
When a new repo/tool is discovered or one of the "genuine gaps" turns out to already be solved, edit this file in place (move it out of the gaps list into the inventory) rather than leaving both an old and new claim standing.
