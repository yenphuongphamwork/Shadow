---
name: agent-self-learning-mechanism
description: "How this agent learns and updates itself over time — the human-in-the-loop rules, grounded in Ownego's AMA/#oe-lab guidance. Governs EVERY write to long-term memory."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 12a24032-5a00-438d-86c3-d8ba57dc88a0
  modified: 2026-09-21T04:05:19.135Z
---

Grounded in the company AMA canvas "[AMA] AI & around it" + #oe-lab discussions (Sept 2026). What the company's AI experts actually said:
- **Sonnh (sonnh): "Đừng để nó update data auto, sau này noise và mess, ko quản lý được."** Never let the agent silently absorb things into its brain. His own agent ("Hans") uses a review/approve step; to add knowledge you feed it a source (e.g. a Slack thread link), it analyzes and saves to brain — with the human in the loop ("mất công hơn xíu mà yên tâm").
- **thangnc → Sonnh (about openclaw): "Cái gì đáng để agent nhớ, cái gì chỉ cần tra lại khi cần? Làm sao long-term memory giữ được qua compaction?"** → the remember-vs-look-up split, and durable files that survive context compaction.
- **tiennhc (AMA): how do you keep the agent improving, not regressing; how do you handle a wrong answer so it doesn't repeat.**
- **Phượng's own AMA/session question: do these agents ever conflict or lead you in circles? how do you detect and fix that?** → the mechanism must have a detection loop, not just a write path.

## The mechanism — 4 parts

### 1. Two speeds of learning (the key distinction)
- **AUTO (no approval)** — ONLY `current-work-state.md`. The catch-up routine mirrors her own weekly self-DM note + the current Action Plan. Safe to auto because it copies her own words, doesn't infer or judge. This is the *only* thing that self-updates silently.
- **PROPOSE-THEN-CONFIRM** — everything else that would change the agent's durable brain: a new fact/tool/rule/number/preference, or a correction she gives. The agent says *"T học được X → định ghi vào [file] thế này, OK không?"* and writes ONLY on her yes. This is Sonnh's "đừng update auto" applied. (This gate is about the agent changing its OWN memory — it's separate from her task-autonomy preference, where small/low-risk *work* just gets done and shown. Doing work ≠ rewriting the brain.)

### 2. Remember-vs-look-up filter (run before ANY write)
Write to memory only if it is **durable + reusable across sessions** (a preference, a rule, a hard-won fact, a pointer to where something lives). Do NOT store: one-offs, or anything already in a repo / git history / Confluence — look those up on demand instead. Keep `MEMORY.md` lean: it's the always-loaded index; every other file is pulled only when the task needs it. (This is exactly the remember-vs-lookup split thangnc asked about, and what keeps the brain from turning into noise.)

### 3. Not regressing (edit protocol)
- Edit the right file **in place** — never stack a contradicting line under an old one.
- Reversing a prior fact → leave `_Corrected <date>: was "..." — now "..."_`.
- Behavioral/process corrections → skill `lessons.md`; tone/voice corrections → skill `voice-notes.md`.
- Everything git-backed → a bad learning can be rolled back; git history is the safety net against regression.

### 4. Detection loop (catch when it's wrong — Phượng's own concern)
- The session-start catch-up + her review of each *proposed* learning IS the detection point — nothing enters the brain unseen.
- `lessons.md` logs each **class** of mistake so the same kind doesn't recur.
- If the agent seems to go in circles or contradict itself, say so out loud and check the relevant memory file for a stale/contradicting entry; fix in place per §3.

## Org patterns borrowed from other Ownego / open agents (Sept 2026 study)
- **pm-brain** (github.com/phuryn/pm-brain — the closest analog, a personal "brain"): confirms the whole design — plain grep-able markdown, **no vector DB / no memory tricks**, files split by *type*, and every fact carries **provenance**. Two things adopted from it below (provenance tags + a weekly drift sweep). Its heavier folders (`hypotheses/`, `ingestion/`, `source/` audit trail) are NOT built — overkill for a marketing agent; available to grow into later if she wants.
- **blacksmith** (github.com/juzser/blacksmith — Sonnh's, a code "factory"): its factory/worktrees/token-budgets are for multi-agent code building — deliberately NOT adopted (her framework = 1 agent, don't over-engineer). But its **"lesson candidates you approve or reject"** = exactly the propose-then-confirm gate above, and its **same-mistake-rate** idea is adopted into `lessons.md` (below).

### Adopted refinements
- **Provenance on every stored fact** (from pm-brain): when writing a memory fact, note where it came from — her Slack note / Confluence / a decision she made in chat / an inference still to confirm. Makes drift detectable and keeps "never fabricate" honest. (The existing memory files already cite sources; make it a rule, not a habit.)
- **Weekly drift sweep** (from pm-brain's `/review`): the weekly scheduled job — and a manual "rà lại memory" on request — scans the memory files for stale or contradicting entries and flags them in the digest for her judgment. This is the active half of §4 (detection), not just passive logging.
- **Same-mistake rate** (from blacksmith): when appending to `lessons.md`, if a logged mistake class recurs, mark it — a recurring one means the lesson isn't working and needs a stronger rule, not another log line.

## Hard "do not"
No fully-autonomous memory absorption. No auto-ingesting external data into the brain without the propose-confirm gate. (The weekly scheduled job may auto-refresh `current-work-state.md` and post a digest, but it must NOT auto-write any other memory file.)

## Update protocol for this file
If the company shares newer guidance on agent learning (another AMA, an #oe-lab post), reconcile it here in place. This file governs the others — keep it the single source of truth for "how the agent learns."
