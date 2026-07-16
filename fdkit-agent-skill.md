---
layout: default
title: Using FdKit — Agent Skill
---

## Using FdKit — Agent Skill

Drop this skill into your **app** repo so Cursor, Claude Code, Codex, or another coding agent knows how to use [FdKit]({{ "/" | relative_url }}) — state, Compose screens, data layer, setup.

Full skill: `[SKILL.md](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md)`.

## Install

Run these from your app repo root.

### Claude Code

Skills under `.claude/skills/` load automatically:

```bash
mkdir -p .claude/skills/using-fdkit
curl -fsSL -o .claude/skills/using-fdkit/SKILL.md \
  https://raw.githubusercontent.com/TrueGrom/truegrom.github.io/master/using-fdkit/SKILL.md
```



### Cursor

```bash
mkdir -p .cursor/skills/using-fdkit
curl -fsSL -o .cursor/skills/using-fdkit/SKILL.md \
  https://raw.githubusercontent.com/TrueGrom/truegrom.github.io/master/using-fdkit/SKILL.md
```



### Codex

Codex picks up repo skills from `.agents/skills/` (ChatGPT desktop app and CLI):

```bash
mkdir -p .agents/skills/using-fdkit
curl -fsSL -o .agents/skills/using-fdkit/SKILL.md \
  https://raw.githubusercontent.com/TrueGrom/truegrom.github.io/master/using-fdkit/SKILL.md
```

Restart Codex if the skill doesn’t show up right away.

### Other agents

Copy the skill file into your agent’s instructions (`AGENTS.md`, project rules, or a system prompt), or into `.agents/skills/using-fdkit/SKILL.md` if the tool supports [Agent Skills](https://agentskills.io). Same file: [raw URL](https://raw.githubusercontent.com/TrueGrom/truegrom.github.io/master/using-fdkit/SKILL.md).

## What's inside

1. **[Installation](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#1-installation)** — BOM, modules
2. **[One-time app setup](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#2-one-time-app-setup)** — logging, `HttpConfigProvider`, Hilt, `FdkScreenDefaults`
3. **[Core utilities](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#3-core-utilities-utils)** — `Result`, `Either`, `Value`
4. **[Data layer](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#4-data-layer-repository-http-error-network)** — `BaseRepository`, `httpSafeCall`, `HttpError`
5. **[State management](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#5-state-management-viewmodel-state--the-core-of-fdkit)** — `StateViewModel`, builders, traits, delegates, `RemoteData`
6. **[Screens](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#6-screens-screen-ui-kit)** — `ViewModelScreen`, `Fetchable`, pull-to-refresh, paging
7. **[Crypto](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#7-crypto-crypto)** — `CryptoManager`, AAD
8. **[Datetime](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#8-datetime-datetime)** — format extensions
9. **[Rules checklist](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md#9-rules-checklist)**

[← Back to FdKit overview]({{ "/" | relative_url }})