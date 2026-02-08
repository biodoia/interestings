# CodyGody Research

Raccolta progetti interessanti per l'ecosistema Biodoia.
Analisi multi-prospettiva: architettura, pattern, idee riutilizzabili.

## Progetti Raccolti

| # | Nome | URL | Stack | Focus |
|---|------|-----|-------|-------|
| 1 | **Squadron** | https://github.com/MikeeBuilds/Squadron | Electron + Python | 6-terminal grid, Kanban, GUI |
| 2 | **vibe-compiler** | https://github.com/Strawberry-Computer/vibe-compiler | Node.js | Self-compiling, prompts-as-code |
| 3 | **Agent of Empires** | https://github.com/njbrake/agent-of-empires | Rust + tmux | TUI, persistent sessions |
| 4 | **Vanna** | https://github.com/vanna-ai/vanna | Python + FastAPI | Text-to-SQL, streaming UI |
| 5 | **Remote Code** | https://remote-code.com/ | iOS | Mobile Claude Code |

## Analisi da Fare

### 1. Architettura
- [ ] Session management (tmux vs pty vs containers)
- [ ] Multi-agent orchestration
- [ ] State persistence
- [ ] IPC / messaging tra agenti

### 2. UI/UX
- [ ] TUI vs GUI vs Web
- [ ] Dashboard patterns
- [ ] Diff view / code review
- [ ] Progress/status indicators

### 3. Isolation
- [ ] Git worktrees
- [ ] Docker sandbox
- [ ] Branch per task
- [ ] Conflict resolution

### 4. Multi-Provider
- [ ] Claude Code, Codex, Gemini, OpenCode, Cursor, Mistral
- [ ] Auto-detection installed agents
- [ ] API key management
- [ ] Model switching

### 5. Integration
- [ ] Jira / Linear / GitHub Issues
- [ ] Slack / Discord notifications
- [ ] CI/CD triggers
- [ ] MCP servers

### 6. Security
- [ ] API key encryption (OS-level)
- [ ] User-aware permissions
- [ ] Audit logs
- [ ] Rate limiting

### 7. Developer Experience
- [ ] Config files (.aoe/, CLAUDE.md, vibec.json)
- [ ] Hooks / plugins
- [ ] CLI vs TUI vs headless
- [ ] Mobile access

## Pattern Comuni Identificati

1. **Git worktrees** — ogni agent/task lavora in branch isolato
2. **tmux backend** — sessioni persistenti
3. **Multi-provider** — switch tra Claude/Codex/Gemini
4. **Status detection** — running/waiting/idle
5. **Per-repo config** — settings specifici per progetto

## Prossimi Passi

1. Clone tutti i repo per analisi codice
2. Estrarre architetture dettagliate
3. Identificare best patterns da fondere
4. Design del mega-agent Autoschei
