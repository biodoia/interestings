# AIAssist

**URL:** https://github.com/mehdihadeli/AIAssist

## Overview
Context-aware AI coding assistant. .NET tool con RAG o Tree-sitter.

## Stack
- **.NET** (dotnet tool install --global AIAssist)
- C#
- Apache-2.0

## Providers
OpenAI, Azure AI, Ollama, Anthropic, OpenRouter, Grok, Gemini, DeepSeek, Qwen

## Feature Chiave
1. **Dual context strategy:**
   - RAG via embeddings
   - Tree-sitter application summarization
2. **Multiple diff formats:**
   - Unified Diff Format
   - Code Block Format
   - Search-Replace Format
3. **Token usage + pricing** — costi calcolati per modello
4. **`.aiassistignore`** — custom ignore separato
5. **`aiassist-config.json`** — per-project config
6. **Custom models info** — override model pricing/info
7. **Syntax highlighting** — Dracula, VSCode themes

## Commands
- `aiassist code` — code assistance
- `aiassist chat` — chat mode
- `aiassist explain` — code explanation
- Internal: `:clear`, `:add-file`, `:clear-history`, `:token`

## Pattern Interessanti
1. **Dual context strategy** — RAG vs Tree-sitter (scelta)
2. **Multiple diff parsers** — formato output configurabile
3. **Model info override** — custom pricing/tokens per modello
4. **Separate embedding model** — chat model ≠ embedding model

## Pro
- .NET ecosystem
- Dual context approach
- Token + pricing tracking
- Flexible diff formats

## Contro
- Richiede .NET SDK
- Meno maturo
- No git integration

## Idee Riutilizzabili
- RAG vs Tree-sitter as config option
- Multiple diff format output
- Custom model pricing configuration
- Separate chat/embedding API keys
