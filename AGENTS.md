# Obsidian Mind

This vault is built for [Claude Code](https://claude.ai/code) with a full operating manual in `CLAUDE.md`.

**Read `CLAUDE.md` for all vault conventions** — structure, note types, linking rules, frontmatter schemas, indexes, and workflows. Most of the content is agent-agnostic.

## Hooks

The hook scripts in `.claude/scripts/` are agent-agnostic Python and shell — no Claude SDK dependencies. Hook configs are provided for three agents:

| Agent | Config | Status |
|-------|--------|--------|
| Claude Code | `.claude/settings.json` | Full support |
| Codex CLI | `.codex/hooks.json` | Shared hook scripts |
| Gemini CLI | `.gemini/settings.json` | Shared hook scripts |

| Script | Purpose | Claude / Codex event | Gemini event |
|--------|---------|---------------------|--------------|
| `session-start.sh` | Inject vault context at startup | SessionStart | SessionStart |
| `classify-message.py` | Classify messages, inject routing hints | UserPromptSubmit | BeforeAgent |
| `validate-write.py` | Validate frontmatter and wikilinks | PostToolUse | AfterTool |
| `pre-compact.sh` | Back up transcript before compaction | PreCompact | PreCompress |

## Commands

18 slash commands in `.claude/commands/` — agent-agnostic markdown with YAML frontmatter. Invoke as `/om-standup`, `/om-dump`, etc. in any agent that supports custom commands or skills.

## What's agent-specific

Subagents (`.claude/agents/`) and the memory system (`~/.claude/`) are Claude Code-only. Skip those sections in `CLAUDE.md`.

## Setup

**Codex CLI**: Reads `AGENTS.md` natively. For direct access to `CLAUDE.md`, add to `~/.codex/config.toml`:
```toml
project_doc_fallback_filenames = ["CLAUDE.md"]
```

**Gemini CLI**: Reads `GEMINI.md` natively. For direct access to `CLAUDE.md`, add to `~/.gemini/settings.json`:
```json
{ "context": { "fileName": ["GEMINI.md", "CLAUDE.md"] } }
```

**Other agents** (Cursor, Windsurf, Copilot): Read `AGENTS.md` for vault conventions. Hook support varies by agent.

For more information, see the [README](README.md).
