# Rulebook-AI

**URL:** https://github.com/botingw/rulebook-ai

## Overview
AI Environment Manager — definisci rules/context/tools una volta, deploya su tutti gli AI assistants.

## Stack
- Python CLI (uv/uvx)
- Pack-based system
- MIT License

## Feature Chiave
- **Packs**: Rules + Context (memory/) + Tools
- **Multi-assistant sync**: Cursor, Copilot, Claude Code, Gemini CLI, Codex CLI, Windsurf, Cline, RooCode, Kilo, Warp
- **Memory bank**: Persistent knowledge base per progetto
- **Profiles**: Named groups of packs per switch rapido
- **Community packs**: light-spec, medium-spec, heavy-spec

## Problema Risolto
- AI forgetful (no long-term memory)
- AI inconsistent (istruzioni non portabili)
- AI unspecialized (generici)

## Pattern Interessanti
1. **Pack = Environment** — rules + context + tools versionabili
2. **Sync to all** — un comando genera per tutti gli assistants
3. **memory/ + tools/** — user-owned, committed to git
4. **.rulebook-ai/** — framework-managed, gitignored
5. **Composable profiles** — mix packs per ruolo/progetto

## Pro
- Universal: funziona con 10+ AI assistants
- Versionable: environment as code
- Community-driven packs
- Clean separation user vs generated

## Contro
- Overhead setup iniziale
- Dipende da formato specifico per ogni AI

## Idee Riutilizzabili per CodyGody
- Pack system per configurazioni
- Sync automatico a formati diversi
- Memory bank persistente
- Profile switching

---

## Pack Developer Guide (Appendice)

### Struttura Pack
```
my-pack/
├── manifest.yaml           # name, version, summary (REQUIRED)
├── README.md               # description (REQUIRED)
├── rules/                  # (REQUIRED)
│   ├── 01-rules/           # general rules
│   │   ├── 00-meta.md
│   │   └── 01-principles.md
│   ├── 02-rules-architect/ # mode-specific
│   └── 03-rules-code/
├── memory_starters/        # (optional) → user memory/
└── tool_starters/          # (optional) → user tools/
```

### manifest.yaml
```yaml
name: My-Awesome-Pack    # unique slug [A-Za-z0-9-]
version: 1.0.0           # semver
summary: One-sentence description
```

### Sync Logic per Assistant Type
1. **Mode-Based** (Roo Code, Kilo): `01-rules/` → `.roo/rules/`, `02-rules-code/` → `.roo/rules-code/`
2. **Multi-File** (Cursor, Cline): all files → `.cursor/rules/` con prefix incrementale
3. **Single-File** (Copilot, Gemini, Warp): concatena tutto in un file

### Validation
```bash
rulebook-ai packs add local:./my-pack  # test locale
rulebook-ai packs remove my-pack       # cleanup
```

### Pattern: pack-authoring-guide
Meta-pack che aiuta a creare altri packs usando AI!
