# Codai

**URL:** https://github.com/meysamhadeli/codai

## Overview
AI coding agent per terminal. Go-based, config-driven.

## Stack
- **Go** (go install github.com/meysamhadeli/codai@latest)
- Chroma per syntax highlighting

## Providers
OpenAI, Azure-OpenAI, Anthropic, Gemini, Grok, DeepSeek, Qwen

## Feature Chiave
1. **Tree-sitter** — summarize full project context
2. **Multi-file editing** — modifica più file simultaneamente
3. **Token tracking** — consumo visualizzato per request
4. **Per-project config** — codai-config.yml
5. **Custom gitignore** — .codai-gitignore
6. **Session context** — mantiene conversazione + code context
7. **Code review** — assistenza review e ottimizzazione

## Config Example
```yaml
ai_provider_config:
  provider: "azure-openai"
  base_url: "https://test.openai.azure.com"
  model: "gpt-4o"
  temperature: 0.2
  reasoning_effort: "low"
theme: "dracula"
```

## Pattern Interessanti
1. **Tree-sitter context** — parse AST per capire struttura progetto
2. **Per-project config** — override globale con file locale
3. **Custom ignore** — .codai-gitignore separato da .gitignore
4. **CLI + config hybrid** — `--provider openai --temperature 0.8`

## Pro
- Go = single binary, veloce
- Tree-sitter = context intelligente
- Config flessibile
- Multi-lang support

## Contro
- Meno maturo di altri
- No RAG built-in
- No git integration

## Idee Riutilizzabili
- Tree-sitter per project summarization
- Per-project config con override CLI
- Token tracking display
- Separate .codai-gitignore
