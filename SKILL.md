---
name: daily-research
description: Automated daily signal-first research digest — cron-driven pipeline that selects themes, researches with web tools, and writes reports to an Obsidian vault. Zero Python, just prompts and a shell wrapper over claude -p.
user-invocable: true
origin: original
---

# daily-research

Autonomous daily research powered by `claude -p` (Claude Code's non-interactive mode) — theme selection with Opus, multi-stage web research with Sonnet, LLM-as-Judge quality evaluation, reports written directly to an Obsidian vault.

**Skill anatomy**: `prompts/` are the skill's core intelligence. `scripts/daily-research.sh` is a thin wrapper that invokes `claude -p` with those prompts. Everything else (tests, launchd plist, config template) is supporting infrastructure.

## When to use

- **Scheduled daily execution** — macOS `launchd` (included) or any cron / systemd setup
- **Manual one-shot run** — `./scripts/daily-research.sh` or invoke via `/daily-research` after installing as a Claude Code skill
- **Background of the skill** — see [AKC ADR-0010](https://github.com/shimo4228/agent-knowledge-cycle/blob/main/docs/adr/0010-human-cognitive-resource-as-central-constraint.md) for the signal-first Research philosophy this implements

## Execution

```bash
./scripts/daily-research.sh
```

Prerequisites, configuration, and scheduling are documented in the main [README](README.md#prerequisites). Operations details (monitoring, troubleshooting) are in [RUNBOOK](docs/RUNBOOK.md).

## Install as a Claude Code skill

```bash
git clone https://github.com/shimo4228/claude-skill-daily-research.git \
  ~/.claude/skills/daily-research
```

After cloning, Claude Code recognizes `SKILL.md` and the skill becomes invocable as `/daily-research`. For automatic daily execution, follow the launchd or cron setup in the main README.

## Documentation

- [README.md](README.md) / [README.ja.md](README.ja.md) — overview, features, quick start, design decisions
- [docs/RUNBOOK.md](docs/RUNBOOK.md) / [docs/RUNBOOK.ja.md](docs/RUNBOOK.ja.md) — operations guide
- [docs/CONTRIB.md](docs/CONTRIB.md) / [docs/CONTRIB.ja.md](docs/CONTRIB.ja.md) — development guide
- [config.example.toml](config.example.toml) — configuration template

## Related

- [AKC ADR-0010 Human Cognitive Resource as Central Constraint](https://github.com/shimo4228/agent-knowledge-cycle/blob/main/docs/adr/0010-human-cognitive-resource-as-central-constraint.md) — the design philosophy this skill implements: Research as signal-first, intake filtered for personal relevance
- [Agent Knowledge Cycle (AKC)](https://github.com/shimo4228/agent-knowledge-cycle) — the broader knowledge cycle this skill sits inside
