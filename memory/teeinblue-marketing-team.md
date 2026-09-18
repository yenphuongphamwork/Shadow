---
name: teeinblue-marketing-team
description: "Teeinblue marketing team structure, roles, cadence, and where the live marketing plan/report lives (Confluence/Slack) — for the teeinblue-marketing skill"
metadata: 
  node_type: memory
  type: project
  originSessionId: 12a24032-5a00-438d-86c3-d8ba57dc88a0
  modified: 2026-09-14T11:10:11.470Z
---

User is **Phượng** (Phạm Yến Phượng, Slack `phuongpy`). Her scope: market report (annual/half-yearly PDF + its gated landing page), key feature promotion plans, other landing pages, email campaigns, AI prompt handbook, ASO/App Store growth, AI-search/LLM optimization, FB/Etsy ads — everything to promote **except** blog/social content and partnership. Full work-style detail: [[phuongpy-work-style]].

**Team map (confirmed via Slack profiles, not just Confluence):**
- **Nguyễn Kiều Trang** (`ktrang`) — marketing **team lead**; sets overall OKRs/plan, pricing-launch marketing, Etsy strategy, runs sprint/monthly meetings. NOT the PO.
- **Đỗ Hồng Trang** (`trangdh`) — the actual **PO** (title: Product Owner); approves feature-announcement content before it posts, approves PRs into [[teeinblue-knowledge-repo]]. Distinct person from ktrang — don't conflate.
- **Content team = Thảo (`thaopp`, Content Marketing) + Hạnh (`hanhpt`, Content Marketing)** — Hạnh: blog optimization, backlinks, Wikipedia, technical SEO, owns the team's Claude-Project content-writing setup ([[teeinblue-content-team-playbook]]). Thảo: new blog writing, social posts, LLM seeding. Both co-author copy on pages Phượng drives strategically.
- **Hiền** (`hiennt`, Graphic Designer) — video/design production support (e.g. promo videos, shorts editing).
- **Minh** (`minhnt`) — Teeinblue's founder; occasionally weighs in on marketing/competitor threads.

**Cadence (from Slack, more current than any single Confluence snapshot):**
- Sprint meeting every other Wednesday ~3pm (Slack reminder "Họp Sprint"), matching the biweekly sprint-style action plans that started H2 2026.
- Monthly retro + next-month-plan meeting, first Monday-ish, ~10am ("Remind họp TIB MKT").
- Feature-announcement content needs `trangdh` (PO) sign-off before posting.

**Where the live plan lives:** Confluence space **TM** ("[teeinblue] Marketing Plan"), cloudId `ownego.atlassian.net`. Structure: year/half hub → "TIB Marketing Plan - Hx 20xx" (OKRs+calendar) → monthly "<Month> - Action Plan" (sprint tables from Jul 2026 on) → half-end "TIB Marketing Report - Hx 20xx" (retro). Known hub IDs: H2 2025 `24832245793`, 2026 hub `25017319428` (→ H1 2026 `25275891773`, H2 2026 `25387991047`) — a new hub appears every ~6 months, use `getConfluencePageDescendants` to find the current one.

**Slack channels that matter**: `#tib-marketers` (official discussion), `#tib-marketing-execution` (daily tasks/sprints), `#tib-mkt-alert` (auto rank tracking), `#oe-lab` (company-wide AI/agent-building knowledge sharing — see [[agent-building-framework]]), `#oe-products` (company-wide weekly scrum — good source for cross-team context).

Full working details (OKR snapshot, report format, ASO/AI-search levers, content rules, messaging shift, case studies, built assets) live in the **`teeinblue-marketing` Claude Code skill** (`~/.claude/skills/teeinblue-marketing/SKILL.md`) — invoke via `/teeinblue-marketing`. That skill is the process/detail reference; this memory is the pointer + team map.

Related: [[teeinblue-knowledge-repo]], [[teeinblue-automation-inventory]], [[teeinblue-content-team-playbook]], [[teeinblue-personalization-report-project]], [[tib-insights-landing-2026]].
