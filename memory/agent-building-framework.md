---
name: agent-building-framework
description: "Ownego's internal framework for how non-tech staff should build a personal Claude agent — shared by the PO (Đỗ Hồng Trang) in #oe-lab; governs how Phượng's own marketing agent should be structured"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 12a24032-5a00-438d-86c3-d8ba57dc88a0
  modified: 2026-09-14T11:10:29.237Z
---

Source: Đỗ Hồng Trang (PO, `trangdh`)'s sharing "Từ skills đến multi agents" in Slack `#oe-lab`, 10/09/2026 + follow-up thread 11/09/2026. This is the company's own stated best practice, not something Phượng or Claude invented — follow it when deciding whether to add a subagent, memory file, or new tool.

## The core principles
1. **Tool first, then Learning, then you have an Agent.** Non-tech should build tools that replace manual work first, then invest time building "learning" (domain knowledge) for the agent. Tool (hands) + Learning (brain) = Agent. → Phượng already has the tool layer ([[teeinblue-automation-inventory]]); the learning layer (these memory files + the skill) is what was missing and is being built now.
2. **1 agent = 1 teammate, not 1 task = 1 agent.** An agent should carry many different responsibilities. Don't fragment into a narrow agent per task.
3. **Only split into a separate agent when the *learning* AND the *tool* are both genuinely different** — her own example: "Agent Hiền" handles most output types fine; a second agent ("Agent Lan Anh") is only needed for UI/UX design work because it needs different learning (understanding portal features) and a different tool (Figma). An orchestrator/"Lead" agent is only needed once there are enough sub-agents that coordinating them by hand gets hard.
4. **Every person should have one agent supporting them.** Multi-agent + orchestration is optional, based on need — don't over-engineer it prematurely.
5. Run it via a Claude desktop/CLI session, or build a dedicated web UI — either is fine.
6. The shared **`teeinblue-knowledge` repo** is the standard "domain knowledge" layer she recommends everyone submodule into their own personal setup — validates using it as the base of this agent from the start.

## Applied to Phượng's own agent
Per principle #2/#3: her work (content-adjacent, ads, email automation, market report, ASO, competitor tracking) mostly shares one learning base (Teeinblue context + her own work style) → **stay as one agent** (the `teeinblue-marketing` skill), not a multi-agent setup. Splitting memory into multiple files ([[teeinblue-marketing-team]], [[teeinblue-content-team-playbook]], [[teeinblue-automation-inventory]], etc.) is an internal organization detail for context economy — it does **not** mean multiple agents; it's one agent reading only the relevant file(s) per task.

## Other patterns seen in the same thread (not yet applied here, note for later if scope grows)
- A more advanced setup: a named orchestrator agent (e.g. "Hans") holding full context as `.md` files, delegating to specialized subagents (dev, QA, researcher...) each with its own skill/criteria — only worth doing once the work is genuinely that varied.
- A support-team pattern: one "master brain" agent holding context + access, classifying incoming tickets out to per-area subagents that each hold their own history file.
- Building an agent that "lives on Slack" persistently (via a local machine + Cloudflare trigger, using a Claude subscription rather than API) is a known, documented pattern internally (`SETUPSLACKAGENT.md`, shared by trangdh) if Phượng ever wants the agent reachable outside a Claude Code session.

## Update protocol
If trangdh (or the team) shares an updated version of this framework, edit this file in place rather than layering a second, possibly contradictory version.
