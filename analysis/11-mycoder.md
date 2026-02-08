# MyCoder

**URL:** https://github.com/drivecore/mycoder

## Overview
AI-powered coding CLI. Self-modifying, parallel sub-agents, GitHub native.

## Stack
- Node.js (npm install -g mycoder)
- Playwright per browser automation
- MIT License

## Providers
Anthropic Claude, OpenAI, Ollama

## Feature Chiave
1. **Sub-agents** — spawn parallel agents per concurrent tasks
2. **Self-modification** — si è scritto e testato da solo
3. **GitHub integration** — issues, PRs, `/mycoder` command in comments
4. **MCP support** — Model Context Protocol per external sources
5. **Message compaction** — auto-manages context window
6. **Interactive corrections** — Ctrl+M per inviare correzioni in-flight
7. **Browser automation** — Playwright + system browser detection
8. **Flexible config** — JS, TS, JSON, YAML, TOML

## Config Locations (in order)
1. mycoder.config.js
2. .mycoder.config.js
3. .config/mycoder.js
4. .mycoder.rc
5. package.json "mycoder" field
6. ~/.config/mycoder/config.js

## Pattern Interessanti
1. **Sub-agent spawning** — parallel task processing
2. **In-flight corrections** — Ctrl+M interrupt
3. **GitHub comment trigger** — /mycoder in issue comments
4. **Message compaction** — auto context management
5. **System browser detection** — usa Chrome/Firefox installati
6. **Human compatible** — usa README.md, shell commands per context

## Pro
- Sub-agents per parallelism
- GitHub native workflow
- MCP support
- Self-improving
- Very flexible config

## Contro
- Node.js dependency
- Richiede Playwright setup

## Idee Riutilizzabili
- Sub-agent parallel execution pattern
- Interactive correction (Ctrl+M) during run
- GitHub comment commands (/mycoder)
- Auto message compaction
- Multi-format config support
