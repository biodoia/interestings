# Agent of Empires (AoE)

**URL:** https://github.com/njbrake/agent-of-empires  
**Licenza:** MIT  
**Stato:** Attivo  
**Linguaggio:** Rust

---

## Overview

Agent of Empires è un **terminal session manager per AI coding agents** su Linux e macOS. Costruito su tmux e scritto in Rust.

Permette di eseguire **multipli AI agents in parallelo** su branch diversi del codebase, ognuno nella propria sessione isolata con sandboxing Docker opzionale.

Core concept: **tmux come layer di persistenza per sessioni AI**.

---

## Stack Tecnologico

| Component | Tecnologia |
|-----------|------------|
| **Linguaggio** | Rust |
| **Session Backend** | tmux |
| **UI** | TUI (Terminal UI) Rust |
| **Sandboxing** | Docker (opzionale) |
| **VCS Integration** | Git worktrees |
| **Packaging** | Homebrew, curl installer, cargo |

---

## Architettura

```
┌─────────────────────────────────────────┐
│              AoE TUI                     │
│  • Session list    • Status detection   │
│  • Diff view       • Keybindings        │
└──────────────────────┬──────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────┐
│             tmux Sessions                │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐   │
│  │Claude   │ │Gemini   │ │Codex    │   │
│  │Session 1│ │Session 2│ │Session 3│   │
│  └────┬────┘ └────┬────┘ └────┬────┘   │
└───────┼──────────┼──────────┼──────────┘
        │          │          │
        ▼          ▼          ▼
┌─────────────────────────────────────────┐
│           Git Worktrees                  │
│  /repo/.worktrees/feat-1/               │
│  /repo/.worktrees/feat-2/               │
│  /repo/.worktrees/feat-3/               │
└─────────────────────────────────────────┘
        │
        ▼ (opzionale)
┌─────────────────────────────────────────┐
│           Docker Containers              │
│  • Isolated filesystem                   │
│  • Shared auth volumes                   │
└─────────────────────────────────────────┘
```

### Persistenza via tmux
- Ogni sessione = tmux session
- Agents continuano a girare quando chiudi TUI
- Riapri `aoe` → tutto è ancora lì

---

## Feature Chiave

### 1. Multi-Agent Support
- Claude Code
- OpenCode
- Mistral Vibe
- Codex CLI
- Gemini CLI
- Auto-detect degli agent installati

### 2. TUI Dashboard
| Key | Action |
|-----|--------|
| `n` | Create session |
| `Enter` | Attach to session |
| `t` | Toggle terminal view |
| `D` | Diff view |
| `d` | Delete session |
| `?` | Help |

### 3. Agent + Terminal Views
Toggle tra AI agent e shell terminal paired con `t`

### 4. Status Detection
Visualizza quali agents sono:
- Running
- Waiting for input
- Idle

### 5. Git Worktrees Integration
```bash
# Add session on new branch
aoe add . -w feat/my-feature -b
```
→ Ogni agent lavora su branch isolato

### 6. Docker Sandboxing
```bash
# Sandboxed session
aoe add --sandbox .
```
- Filesystem isolato
- Auth volumes condivisi
- Sicurezza extra per agents untrusted

### 7. Per-Repo Config
`.aoe/config.toml` per settings project-specific e hooks

### 8. Profiles
Workspaces separati per progetti/clienti diversi

---

## Pattern Interessanti

### 1. **tmux-as-Persistence Layer**
Problema risolto elegantemente: sessions che sopravvivono alla chiusura del tool.
tmux è il "daemon" invisibile.

### 2. **Terminal Pairing**
Ogni agent session ha una shell terminal associata → debug, comandi manuali senza uscire dal flusso.

### 3. **Status Detection**
Parsing output per determinare stato agent (running/waiting/idle) → feedback visivo immediato.

### 4. **Worktree-per-Session**
Come Squadron, ma più lightweight (no Electron, no Python).

### 5. **Sandboxing Opzionale**
Docker come layer di isolamento → esegui agents untrusted senza rischi.

### 6. **Detach Pattern**
`Ctrl+b d` → detach e torna a TUI. Pattern tmux nativo riutilizzato.

---

## Pro/Contro

### ✅ Pro
- **Lightweight**: Rust + tmux, no Electron bloat
- **Fast**: binary nativo, TUI veloce
- **Persistente**: tmux sessions sopravvivono
- **Cross-platform**: Linux + macOS
- **Sandboxing**: Docker per isolamento
- **Minimal deps**: solo tmux required

### ❌ Contro
- **Solo terminal**: no GUI, no web
- **Learning curve tmux**: devi conoscere keybindings
- **No Windows**: Linux/macOS only
- **Status detection**: può fallire con output non standard
- **Meno visual**: Kanban e features simili assenti (vs Squadron)

---

## Idee Riutilizzabili

1. **tmux-as-Backend Pattern**
   - Usa tmux per persistenza sessioni
   - Wrap con TUI/CLI per UX migliore
   - `tmux new-session -d` per background work

2. **Terminal Pairing**
   - Ogni sessione AI ha shell associata
   - Toggle rapido per debug

3. **Status Detection via Output Parsing**
   - Analizza output terminale per determinare stato
   - Pattern per qualsiasi CLI wrapper

4. **Docker Sandboxing for Agents**
   - Mount solo auth volumes, isola resto
   - Sicuro per agents che eseguono codice

5. **Worktree CLI Integration**
   - `-w branch-name -b` per creare worktree+branch
   - Pattern semplice da replicare

6. **Per-Repo Config**
   - `.aoe/config.toml` nel repo
   - Hooks e settings project-specific

---

## Confronto con Squadron

| Feature | Agent of Empires | Squadron |
|---------|------------------|----------|
| Stack | Rust + tmux | Electron + Python |
| UI | TUI | GUI |
| Weight | ~10MB | ~200MB+ |
| OS | Linux/macOS | Windows (soon others) |
| Sandboxing | Docker | No |
| Kanban | No | Sì |
| Visual | Minimal | Rich |

---

## Note Personali

AoE è la versione "Unix philosophy" di Squadron: fa una cosa sola (session management) e la fa bene. L'uso di tmux come persistence layer è geniale - leveraggia tooling esistente invece di reinventare.

Perfetto per chi:
- Lavora principalmente in terminal
- Vuole qualcosa di leggero e veloce
- Non ha bisogno di Kanban/visual management

**Interessante per**: pattern tmux-as-backend, sandboxing agents, TUI in Rust.
