---
layout: default
title: Using FdKit — Agent Skill
---

## Using FdKit — Agent Skill

[`SKILL.md`](https://github.com/TrueGrom/truegrom.github.io/blob/master/using-fdkit/SKILL.md) — a guide for AI agents building Android features with [FdKit]({{ "/" | relative_url }}): state, Compose screens, data layer, setup.

**Skill name:** `using-fdkit`

**When to use:** writing or reviewing code that consumes FdKit — `StateViewModel`, builder traits, `RemoteData`, one-shot actions and error reactions, `FdKitBaseScaffold` / `ViewModelScreen`, `BaseRepository`, Ktor client, `CryptoManager`, `FdkLog`, datetime formatters.

## Installation

Copy into your **app** repo (not the FdKit library repo).

### Claude Code

`.claude/skills/<skill-name>/SKILL.md` is picked up automatically.

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

Or add a rule in `.cursor/rules/` pointing at that file.

### Other agents

Use project rules, `AGENTS.md`, or a system prompt — same [raw URL](https://raw.githubusercontent.com/TrueGrom/truegrom.github.io/master/using-fdkit/SKILL.md).

## Contents

1. **Installation** — BOM, modules  
2. **One-time app setup** — logging, `HttpConfigProvider`, Hilt, `FdkScreenDefaults`  
3. **Core utilities** — `Result`, `Either`, `Value`  
4. **Data layer** — `BaseRepository`, `httpSafeCall`, `HttpError`  
5. **State management** — `StateViewModel`, builders, traits, delegates, `RemoteData`  
6. **Screens** — `ViewModelScreen`, `Fetchable`, pull-to-refresh, paging  
7. **Crypto** — `CryptoManager`, AAD  
8. **Datetime** — format extensions  
9. **Rules checklist**

---

[← Back to FdKit overview]({{ "/" | relative_url }})
