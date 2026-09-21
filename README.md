# Shadow

> **Shadow = Phượng's shadow** — cái bóng đi làm hết đống task marketing thay bạn. (Đây là agent cá nhân của Phượng.)

Phượng's (Phạm Yến Phượng) personal marketing agent for Teeinblue — the durable, portable, version-controlled **home** for the agent's brain, learning, and structure. Built following Ownego's internal "Tool + Learning = Agent" framework (see `memory/agent-building-framework.md`).

> **Status: khung (skeleton).** This is the scaffold — structure + assembled pieces. It will be refined over time. It is NOT the live runtime by itself (see "How this maps to live Claude Code" below).

## What this agent is

One agent (not multi-agent) that supports Phượng across her whole marketing scope at Teeinblue: market report, key-feature promotion, landing pages, email, ASO/AI-search, ads, competitor tracking, and brainstorming/decisions — everything except blog/social content (content team's lane) and partnership. Full role/scope: `memory/teeinblue-marketing-team.md`.

## Structure

```
Shadow/
├── CLAUDE.md      # the agent brain — loaded as project instructions when Claude Code opens this folder
├── README.md      # this file
├── tools.md       # index of Phượng's tools + when the agent routes to each
├── knowledge/     # git submodule → github.com/ownego/teeinblue-knowledge (shared domain KB)
└── memory/        # the agent's learning/findings (git-backed durable copies)
```

The runtime logic (task router, catch-up routine, content rules, process) lives in the **`teeinblue-marketing` Claude Code skill** (`~/.claude/skills/teeinblue-marketing/`, backed up to the `Personal-Claude-Skills` repo). This repo is the *home/documentation/portability* layer; the skill is the *runtime behavior* layer.

## How this maps to live Claude Code (important)

The live agent runs from two Claude-Code-managed locations, NOT from this repo directly:
- **Skill**: `~/.claude/skills/teeinblue-marketing/SKILL.md` (+ `voice-notes.md`, `lessons.md`) — pushed to `Personal-Claude-Skills`.
- **Memory**: `~/.claude/projects/-Users-yenphuongpham-Linh-tinh/memory/` — the always-loaded auto-memory (index in its `MEMORY.md`). This is where memory is read/written during real sessions.

`memory/` in THIS repo is a **git-backed mirror** of the agent-specific learning files from that live memory dir (which is otherwise not under version control — so this repo is also its backup). When a memory file changes in a live session, copy it here and push. The live `MEMORY.md` index is the runtime superset (it also holds broader Teeinblue-domain memories not all mirrored here yet).

## Reconstitute on a new machine
1. Clone this repo, then `git submodule update --init` to pull `knowledge/`.
2. Clone her tool repos (see `tools.md`) into `~/github/`.
3. Install the `teeinblue-marketing` skill (clone `Personal-Claude-Skills` into `~/.claude/skills/`).
4. Restore `memory/` files into the Claude Code memory dir for the project.

## Related repos
- `teeinblue-knowledge` (submodule here) — shared domain KB, PO (Đỗ Hồng Trang) approves PRs.
- `Personal-Claude-Skills` — the `teeinblue-marketing` + `market-report-writer` skills.
- Tool repos: `TIB-Grafana-Query`, `TIB-Newsletter-Photo-Uploader`, `TIB-Expert-Page-Updater`, `TIB-Shopify-Community-Thread-Scan`, `blog-automation` — see `tools.md`.
