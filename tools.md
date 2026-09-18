# Tools Phượng already has

Canonical detail + gotchas: `memory/teeinblue-automation-inventory.md`. **Check that file before ever proposing to build a new tool** — a past mistake was proposing to build things that already existed.

This is the routing index: task → tool → what to check first. (Mirrors the skill §1b router table.)

| Task she names | Tool / route | Repo (in `~/github/`) | Check first |
|---|---|---|---|
| newsletter / bản tin | Newsletter pipeline | `TIB-Newsletter-Photo-Uploader` | needs copy+images+date; **stops after test send** — never auto-send real lists; she schedules the real send |
| query số / data / metric | Grafana query CLI (`gq`) | `TIB-Grafana-Query` | read `MARKET_REPORT_STATUS.md`; reuse existing queries; bad `usages` rows, layer-`type` trap, DB-load timing; ⬜ term → ask |
| thêm expert / Hire an Expert page | Expert page updater | `TIB-Expert-Page-Updater` | reads expert Form/Sheet; preview before write; fix languages/price/services |
| seeding Shopify Community | Thread scanner (already scheduled Mon+Thu) | `TIB-Shopify-Community-Thread-Scan` | read latest ranked threads — don't rebuild |
| viết / optimize blog | Blog pipeline (content team's) | `blog-automation` | NOT her lane → route to Thảo/Hạnh, offer a brief |
| market report content section | `market-report-writer` skill | (skill) | its rubric |
| viết copy she owns (landing/feature/in-app/email/ad) | no tool — do it | — | content-team voice + word-format; never fabricate stats |
| landing/feature page on Shopify theme | she codes frontend via AI herself | — | `tib-shopify-theme-reference` memory; dev (Phát) only for backend |
| so sánh đối thủ | no tool yet (manual gap) | — | WebSearch, fact-check before conceding |
| FB / Etsy ads | no tool yet (manual gap) | — | she logs by hand |

## Connectors available to the agent
Atlassian (Confluence/Jira), Brevo (email), Google Drive, Slack, visualize. Grafana is via the `gq` CLI, not a connector.

## Genuine gaps (candidates for future tools — verify still true before building)
1. Ads performance (FB/Etsy) tracking — still manual.
2. Competitor snapshot — still manual.
