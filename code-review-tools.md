# AI Code Review Tools 🔍

Raccolta completa di tool per AI code review.
Fonte: ricerca GitHub, febbraio 2026.

## 🏆 Top Tier (1000+ ⭐)

| Stars | Nome | Descrizione | Language |
|-------|------|-------------|----------|
| 10096⭐ | [pr-agent](https://github.com/qodo-ai/pr-agent) | 🚀 The Original Open-Source PR Reviewer (Qodo/Codium) | Python |
| 7638⭐ | [sweep](https://github.com/sweepai/sweep) | AI-powered PR automation - turns issues into PRs | Python |
| 1782⭐ | [sourcery](https://github.com/sourcery-ai/sourcery) | Instant AI code reviews | Python |
| 897⭐ | [kodus-ai](https://github.com/kodustech/kodus-ai) | AI code reviews — just like your senior dev would do | TypeScript |

## 🥈 Mid Tier (100-999 ⭐)

| Stars | Nome | Descrizione | Language |
|-------|------|-------------|----------|
| 323⭐ | [codeball-action](https://github.com/sturdy-dev/codeball-action) | 🔮 Codeball – AI Code Review that finds bugs and fast-tracks your code | TypeScript |
| 310⭐ | [superclaude](https://github.com/gwendall/superclaude) | Give Claude AI superpowers for GitHub workflows | Shell |
| 273⭐ | [awesome-coderabbit](https://github.com/coderabbitai/awesome-coderabbit) | Curated list of CodeRabbit resources | - |
| 271⭐ | [Easy-AI-CodeReview](https://github.com/spherical-up/Easy-AI-CodeReview) | High-efficiency Code Review tool | Python |
| 228⭐ | [gemini-ai-code-reviewer](https://github.com/truongnh1992/gemini-ai-code-reviewer) | GitHub Action using Google's Gemini AI | Python |
| 138⭐ | [coderabbit-docs](https://github.com/coderabbitai/coderabbit-docs) | Official CodeRabbit documentation | TypeScript |

## 🥉 Rising Stars (20-99 ⭐)

| Stars | Nome | Descrizione | Language |
|-------|------|-------------|----------|
| 89⭐ | [ai-code-reviewer](https://github.com/buxuku/ai-code-reviewer) | OpenAI API for GitLab MR code review | TypeScript |
| 75⭐ | [ai-code-review-helper](https://github.com/Usagi-org/ai-code-review-helper) | Automated code review with webhooks + WeChat integration | Python |
| 62⭐ | [codingfox](https://github.com/furudo-erika/codingfox) | Open Source AI Code Review Tool that Works Like Magic! | TypeScript |
| 57⭐ | [CodeReviewAgent](https://github.com/gitbito/CodeReviewAgent) | On-demand, context-aware AI code reviews in Git/IDE | Shell |
| 50⭐ | [scanline](https://github.com/ScanLineDev/scanline) | Expert AI code reviews CLI - finds race conditions, security risks | Python |
| 46⭐ | [cf_ai_code_review](https://github.com/FelixNg1022/cf_ai_code_review) | AI code review on Cloudflare Workers | TypeScript |
| 43⭐ | [ai-code-review](https://github.com/bobmatnyc/ai-code-review) | Multi-provider CLI (Gemini, Claude, OpenAI) with 95%+ token reduction | TypeScript |
| 38⭐ | [crev](https://github.com/vossenwout/crev) | CLI tool to bundle codebase and get AI reviews | **Go** |
| 33⭐ | [ivan](https://github.com/ariso-ai/ivan) | AI Dev Assistant - tasks → PRs → reviews → fixes | TypeScript |
| 27⭐ | [ai-code-reviewer](https://github.com/jordanhubbard/ai-code-reviewer) | Universal AI reviewer using vLLM/Ollama local LLMs | Python |
| 26⭐ | [maestro](https://github.com/XiaoConstantine/maestro) | Local AI code review assistant built on dspy-go | **Go** |
| 22⭐ | [revu](https://github.com/proDreams/revu) | Self-hosted AI code review for PRs | Python |
| 21⭐ | [diff0](https://github.com/eersnington/diff0) | AI Code Review for GitHub - OSS CodeRabbit/Greptile | TypeScript |
| 18⭐ | [auditlm](https://github.com/ellenhp/auditlm) | Self-hostable AI code review for Forgejo | **Rust** |

## 🎯 Pattern Chiave Identificati

### Architettura
- **GitHub Actions** — La maggior parte sono GitHub Actions
- **Webhook-based** — Ascoltano PR events, analizzano diff
- **Multi-provider** — Supporto OpenAI/Claude/Gemini/Ollama

### Modelli di Integrazione
1. **GitHub Action** — Drop-in, zero config
2. **CLI locale** — Per review pre-commit
3. **Bot PR** — Commenta automaticamente sulle PR
4. **Self-hosted** — Per privacy/compliance

### Funzionalità Comuni
- Analisi diff (hunks, files changed)
- Security scanning
- Performance suggestions
- Code style feedback
- Auto-fix suggestions
- Token optimization (chunking, summarization)

## 🚀 Interessanti per GoView

### CLI-based (come il nostro goview)
- **crev** (Go) — Bundle codebase + AI review
- **maestro** (Go) — Local review con dspy-go
- **scanline** (Python) — CLI per race conditions, security
- **ai-code-review** (TS) — Multi-provider, 95% token reduction

### Self-hosted
- **revu** — Self-hosted per PR
- **auditlm** — Per Forgejo (Rust)
- **ai-code-reviewer** — vLLM/Ollama support

### Multi-Provider Pattern
```
Provider Priority: OpenRouter → Anthropic → OpenAI → Groq → Ollama
Auto-detect API keys from environment
Fallback to local model (Ollama) when no keys
```

## 📋 Da Analizzare in Dettaglio

1. **pr-agent** — Il reference implementation (10k⭐)
2. **sweep** — Automazione completa issue→PR
3. **crev** — Go CLI, pattern simile a goview
4. **maestro** — Go + dspy-go, interessante per DSPy patterns

## 🔗 Servizi SaaS (per reference)
- [CodeRabbit](https://coderabbit.ai) — AI code reviews as a service
- [Sourcery](https://sourcery.ai) — Instant AI reviews
- [Codium/Qodo](https://qodo.ai) — PR-Agent commercial
- [Greptile](https://greptile.com) — AI code search + review
