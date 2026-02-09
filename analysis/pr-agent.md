# PR-Agent Analysis 🚀

> The Original Open-Source PR Reviewer (10k+ ⭐)
> https://github.com/qodo-ai/pr-agent

## Overview

PR-Agent di Qodo (ex-Codium) è il reference implementation per AI code review.
Ora community-maintained, donato a una foundation open-source.

## Architettura

```
┌─────────────────┐
│   Git Provider  │  GitHub, GitLab, Bitbucket, Azure DevOps, Gitea
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   PR-Agent      │  Single LLM call per tool (~30s, low cost)
│                 │
│  ┌───────────┐  │
│  │ /describe │  │  Auto-generate PR description
│  │ /review   │  │  Code review with issues
│  │ /improve  │  │  Suggest improvements
│  │ /ask      │  │  Q&A on code
│  └───────────┘  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   LLM Backend   │  OpenAI, Claude, Deepseek, etc.
└─────────────────┘
```

## Core Features

### Tools disponibili
| Tool | Descrizione |
|------|-------------|
| `/describe` | Auto-genera descrizione PR |
| `/review` | Code review con issue detection |
| `/improve` | Suggerimenti di miglioramento |
| `/ask` | Q&A sul codice |
| `/update_changelog` | Aggiorna CHANGELOG automaticamente |

### Deployment Options
1. **GitHub Action** (raccomandato) - zero config
2. **CLI** - `pip install pr-agent && pr-agent --pr_url URL review`
3. **Webhook** - self-hosted
4. **Docker** - containerizzato

## Pattern Chiave

### PR Compression Strategy
- Gestisce PR di qualsiasi dimensione
- Adaptive token-aware file patch fitting
- Chunking intelligente

### Single LLM Call
- Ogni tool usa UNA sola chiamata LLM
- ~30 secondi di latenza
- Costo contenuto

### Configuration via TOML
```toml
# pr_agent/settings/configuration.toml
[pr_review]
require_all_thresholds_for_approval = false
num_code_suggestions = 4

[github]
publish_inline_comments_fallback = true
```

### JSON-based Prompting
- Prompts customizzabili
- Output strutturato
- Facile da estendere

## Cosa Copiare per GoView

1. **Tool modulare** - comandi separati `/review`, `/describe`, `/improve`
2. **PR Compression** - gestione PR grandi con chunking
3. **Multi-provider** - supporto OpenAI/Claude/Deepseek
4. **Config file** - TOML per settings
5. **GitHub Action** - deployment automatico

## Limitazioni

- Python-based (noi vogliamo Go)
- Dipendenza da Qodo ecosystem
- Ora community-maintained (meno updates)

## Relevanza per GoView

| Feature | PR-Agent | GoView |
|---------|----------|--------|
| Language | Python | **Go** |
| CLI | ✅ | ✅ |
| Multi-provider | ✅ | ✅ |
| GitHub Action | ✅ | ❌ (futuro) |
| Local/Ollama | ❌ | ✅ |
| TUI | ❌ | ✅ (lipgloss) |
