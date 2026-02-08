# Interestings

Raccolta progetti interessanti per l'ecosistema Biodoia.
Analisi multi-prospettiva: architettura, pattern, idee riutilizzabili.

Framework di riferimento: **framegotui** (Go + Bubble Tea + ConnectRPC)

## Progetti Raccolti

| # | Nome | Focus |
|---|------|-------|
| 1 | **Squadron** | 6-terminal grid, Kanban, GUI |
| 2 | **vibe-compiler** | Self-compiling, prompts-as-code |
| 3 | **Agent of Empires** | TUI, persistent sessions, tmux |
| 4 | **Vanna** | Text-to-SQL, streaming UI |
| 5 | **Remote Code** | Mobile Claude Code |
| 6 | **Serena MCP** | LSP-based semantic code understanding |
| 7 | **Multi-Agent Squad** | Multi-agent orchestration framework |

## Categorie di Analisi

### Architettura
- Session management (tmux vs pty vs containers)
- Multi-agent orchestration
- State persistence
- IPC / messaging tra agenti

### UI/UX
- TUI vs GUI vs Web
- Dashboard patterns
- Diff view / code review
- Progress/status indicators

### Isolation
- Git worktrees
- Docker sandbox
- Branch per task
- Conflict resolution

### Multi-Provider
- Claude Code, Codex, Gemini, OpenCode, Cursor, Mistral
- Auto-detection installed agents
- API key management
- Model switching

### Integration
- Jira / Linear / GitHub Issues
- Slack / Discord notifications
- CI/CD triggers
- MCP servers

### Security
- API key encryption (OS-level)
- User-aware permissions
- Audit logs
- Rate limiting

## Pattern Comuni Identificati

1. **Git worktrees** — ogni agent/task lavora in branch isolato
2. **tmux backend** — sessioni persistenti
3. **Multi-provider** — switch tra Claude/Codex/Gemini
4. **Status detection** — running/waiting/idle
5. **Per-repo config** — settings specifici per progetto
6. **LSP integration** — semantic code understanding (Serena)
7. **Specialized agents** — ruoli specifici invece di AI monolitica
8. **MCP servers** — estendere capabilities via protocollo standard
