# Obsidian Mind

An Obsidian vault that makes Claude Code remember everything.

## The Problem

Claude Code is powerful, but it forgets. Every session starts from zero — no context on your goals, your team, your patterns, your wins. You re-explain the same things. You lose decisions made three conversations ago. The knowledge never compounds.

## The Solution

Give Claude a brain. This vault is a structured knowledge base that Claude reads at the start of every session and writes to as you work. Your goals, decisions, patterns, people context, and work history persist across conversations. Every session builds on the last.

The result: Claude becomes a genuine thinking partner instead of a stateless tool. It knows your codebase patterns, remembers your gotchas, tracks your wins for performance reviews, and maintains a graph of connected notes that grows smarter over time.

## How It Works

```
You: "start session"
Claude: *reads North Star, checks active projects, scans recent memories*
Claude: "You're working on Project Alpha, blocked on the BE contract.
         Last session you decided to split the coordinator. Your 1:1
         with your manager is tomorrow — review brief is ready."
```

This happens because the vault gives Claude persistent context through:

- **`brain/`** — Claude's operational memory (decisions, patterns, gotchas)
- **`work/`** — Your projects, incidents, meetings, decisions
- **`perf/`** — Brag doc, competency evidence, review briefs
- **`org/`** — People, teams, relationships
- **`bases/`** — Dynamic database views over all your notes
- **`Home.md`** — Dashboard with embedded views, your starting point

## What's Inside

### Slash Commands

Eight workflows you can invoke directly:

| Command | What It Does |
|---------|-------------|
| `/peer-scan` | Scans a colleague's GitHub PRs and produces a structured review analysis |
| `/slack-scan` | Extracts evidence from Slack channels — timestamped, organized by context |
| `/capture-1on1` | Turns a meeting transcript into a structured note with quotes and action items |
| `/vault-audit` | Deep audit of your vault — finds broken links, stale context, missing frontmatter |
| `/review-brief` | Generates a performance review brief from your vault data |
| `/incident-capture` | Takes incident Slack URLs and produces a full timeline, root cause analysis, and brag entry |
| `/project-archive` | Moves a completed project to archive, updates all indexes |
| `/wrap-up` | End-of-session review — verifies everything, suggests improvements |

### Obsidian Bases

Seven dynamic database views that replace manual index maintenance:

| Base | Shows |
|------|-------|
| Work Dashboard | All work notes grouped by quarter, filterable by status |
| Incidents | Incident overview with severity, your role, ticket reference |
| People Directory | Everyone you work with, grouped by team |
| 1:1 History | All meeting notes, chronological |
| Review Evidence | PR scans and evidence, filterable by person and review cycle |
| Competency Map | Your competencies with evidence count from backlinks |
| Templates | Quick reference for available note templates |

### Hooks

Three automated behaviors in `.claude/settings.json`:

- **SessionStart** — Injects the full vault file listing into context. Claude knows what exists without wasting turns on file discovery.
- **PreToolUse** — Before creating any `.md` file, reminds Claude about frontmatter requirements and linking conventions.
- **Stop** — End-of-session checklist: archive completed work, update indexes, check for orphaned notes.

## Quick Start

1. Use this repo as a **GitHub template** (or clone it)
2. Open the folder as an **Obsidian vault**
3. Enable **Bases** in Settings > Core plugins
4. Enable the **Obsidian CLI** in Settings > Core plugins (requires Obsidian 1.12+)
5. Run **`claude`** in the vault directory
6. Fill in **`brain/North Star.md`** with your current goals

That's it. Claude reads `CLAUDE.md` automatically and understands the full structure.

## Vault Structure

```
Home.md                    Dashboard — open this first
CLAUDE.md                  Claude's operating manual (auto-loaded)

bases/                     Dynamic database views
brain/                     Claude's persistent memory
  Memories.md                Topic index
  Key Decisions.md           Architectural decisions
  Patterns.md                Recurring patterns
  Gotchas.md                 Known pitfalls
  Skills.md                  Workflow documentation
  North Star.md              Your goals (read every session)

work/                      Everything you're working on
  Index.md                   Central map of content
  active/                    Current projects (small, focused)
  archive/                   Completed work by year
  incidents/                 Incident docs and root cause analyses
  1-1/                       Meeting notes

perf/                      Performance tracking
  Brag Doc.md                Running log of wins
  brag/                      Quarterly brag notes
  competencies/              Your org's competency framework
  evidence/                  PR scans and review data

org/                       People and teams you work with
  People & Context.md        Index of relationships and dynamics
  people/                    One note per person
  teams/                     One note per team

reference/                 Codebase knowledge, architecture docs
templates/                 Note templates with frontmatter
thinking/                  Scratchpad for reasoning before committing
```

## Customize It

This is a starting point. Adapt it to how you work:

- **`brain/North Star.md`** — Write your goals. This grounds every session.
- **`perf/competencies/`** — Create notes matching your org's competency framework
- **`org/`** — Add your manager, team, key collaborators
- **`.claude/commands/`** — Edit commands to match your tools (GitHub org, Slack workspace)
- **`CLAUDE.md`** — The operating manual. Update conventions as your workflow evolves.

## Requirements

- [Obsidian](https://obsidian.md) 1.12+
- [Claude Code](https://claude.ai/claude-code)
- Bases core plugin enabled
- Git for version history

## Design Influences

- [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) — Official Obsidian agent skills
- [James Bedford](https://x.com/jameesy) — Vault structure philosophy
- [arscontexta](https://github.com/agenticnotetaking/arscontexta) — Progressive disclosure, session hooks

## License

MIT
