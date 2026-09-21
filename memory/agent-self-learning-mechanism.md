---
name: agent-self-learning-mechanism
description: "How this agent learns and updates itself over time — human-in-the-loop rules grounded in Ownego's AMA (Sơn's answers) + #oe-lab. Governs EVERY write to long-term memory. Keep it lean."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 12a24032-5a00-438d-86c3-d8ba57dc88a0
  modified: 2026-09-21T04:21:19.961Z
---

Source: the company AMA "[AMA] AI & around it" — **Sơn (sonnh)'s written answers** (pasted by Phượng 2026-09-21) — plus #oe-lab threads. Sơn's caveat: no structure is "standard"; these optimize, but adapt to the specific agent. His overarching advice: **keep it super lean, one agent = one problem, minimize the data you must maintain** (OEditions S7 even argued "2nd brain nhiều khi không thực sự hữu dụng" — don't let this bloat into an unused brain).

## 1. Two speeds of learning
- **AUTO (no approval)** — ONLY `current-work-state.md` (the catch-up mirrors her own notes; copies, doesn't infer).
- **PROPOSE-THEN-CONFIRM** — every other write to the brain. Agent says *"t học được X → định ghi vào [file] thế này, OK không?"*, writes only on her yes. Sơn: **"Mọi data được ghi vào nên do người quyết định"** — the human appears at the right moment, approve/reject. (This gates *memory writes* — separate from her task-autonomy pref, where small *work* just gets done.)

## 2. Remember vs look-up + static vs dynamic
- Store only durable, reusable facts/prefs/rules/pointers. One-offs or things already in a repo/git/Confluence → look up on demand, don't store. Keep `MEMORY.md` lean (always-loaded index).
- **Static data** (stable knowledge, rules, prefs) → skill / prompt `.md` (memory files). **Dynamic data** (changes often, e.g. work-state) → the auto-refreshed file. Don't mix them.
- Deciding *which file* a fact belongs in is a job to do well (Sơn runs a "librarian" subagent for it; for our single-agent that's just a rule the agent follows, not a new agent) — put each fact in its one right place, don't duplicate across files.

## 3. Fixing wrong info — do NOT annotate, actually FIX (Sơn's explicit warning)
- Sơn: if you just tell it "this is wrong, đừng lặp lại", the **old wrong data stays** and it appends a "this is wrong" line → **data thành rác**. So: when a fact is wrong, **correct or delete the wrong content cleanly**, don't stack a "this was wrong" line under it.
- Only for a genuine *reversal of understanding* (not plain error) leave `_Corrected <date>: was "..." — now "..."_` so history is legible. Everything git-backed → real rollback if needed.

## 4. Lesson mechanism (Sơn's model — for recurring mistakes)
Not every mistake becomes a lesson (that's noise). Instead:
- Let a mistake happen a few times, but the agent must **notice it's repeating** (track recurrence; Sơn's rough thresholds: small errors ~5–10 repeats, big errors <5).
- On reaching the threshold → **escalate to Phượng**: "lỗi này lặp N lần rồi, solution nên là gì?" → **she gives the solution**.
- Save that as a **lesson in `lessons.md`, kept separate from knowledge** (it's a fix-recipe, not a fact). Next time the agent hits that error, it looks up the lesson and already has her solution.
- A lesson that keeps recurring after being logged = the rule is too weak → strengthen it, don't just re-log.

## 5. Detection + resurfacing (catch stale/wrong — Phượng's own AMA concern)
- Session-start catch-up + her review of each proposed write = nothing enters the brain unseen.
- **Staleness resurfacing** (Sơn's): the weekly job (and on-request "rà lại memory") flags facts that look outdated, unused, or untouched >~14 days → surfaces them in the digest as "vẫn đúng / cần chỉnh?" for her to confirm. It flags, never auto-fixes.
- If the agent contradicts itself / goes in circles, say so and check the relevant file for a stale entry; fix per §3.

## 6. Future capture mechanisms (from Hans — need the deferred always-on/Slack+dashboard setup; not built yet)
When/if she sets up the always-on Slack agent, these become possible; until then the manual equivalent is "point at it and say nhớ cái này":
- **Slack-reaction capture**: react to a message → agent briefs/summarizes → proposes to save (insight/calendar/note).
- **Daily journal**: agent asks a few fixed + flexible questions, she picks answers → captured.
- **Monthly public-source scan**: re-scan website/branding/public blogs to refresh info.
- **Weekly summary → proposed insights → approve/reject inbox** (her weekly digest already does the summary; the "proposed insights to approve" is the piece to add when there's a dashboard/inbox).

## Org patterns borrowed (Sept 2026 study) — condensed
- **pm-brain**: confirms grep-able markdown, no vector DB; adopted provenance tags + weekly drift sweep. Its heavy folders (`hypotheses/`, `ingestion/`, `source/`) NOT built (bloat).
- **blacksmith** (Sơn's code factory): its factory/worktrees/token-budgets NOT adopted (1-agent). Its "lesson candidates you approve/reject" = the §4 lesson mechanism.
- **Provenance**: tag each stored fact with source (her Slack note / Confluence / a decision in chat / an inference-to-confirm).

## Subagent economy (only when delegating per skill §11b)
If spawning subagents for parallel work: reserve the strong model for planning/synthesis; grunt work (research, first-draft, data pulls) can use a cheaper model. Sơn's core point: **the win is in detailed planning up front (human + strong model)** — then cheap models execute well. Don't over-summon; one agent stays the default.

## Hard "do not"
No fully-autonomous memory absorption. No auto-ingesting external data into the brain without the propose-confirm gate. Don't let md files grow large or overlap. (The weekly job may auto-refresh `current-work-state.md` + post a digest, but must not auto-write any other memory file.)

## Update protocol
Newer company guidance (another AMA/#oe-lab) → reconcile here in place. This file governs the others.
