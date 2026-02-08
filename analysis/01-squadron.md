# Squadron - Agentic Operating System for Desktop

**URL:** https://github.com/MikeeBuilds/Squadron  
**Licenza:** AGPL-3.0  
**Stato:** Attivo (v2.0)

---

## Overview

Squadron è un "sistema operativo agentico" desktop che permette di gestire swarm di AI agents locali (Gemini, Claude, Codex) come se fossero dipendenti. È un command center nativo che combina:
- Gestione parallela di 6 terminali AI
- Kanban board per task management
- Integrazione deep con Jira/Linear

L'idea core: **trasformare l'autonomia degli AI agents in lavoro ingegneristico reale**.

---

## Stack Tecnologico

| Layer | Tecnologia |
|-------|------------|
| **Desktop Shell** | Electron |
| **Frontend** | React + Vite |
| **Terminal** | xterm.js + node-pty |
| **Backend** | Python (FastAPI) |
| **IPC** | Electron IPC |
| **Storage API Keys** | OS-level encryption (DPAPI/Keychain) |

---

## Architettura

```
┌─────────────────────────────────────────────────────────┐
│                    ELECTRON SHELL                        │
│  ┌─────────────────┐    ┌────────────────────────────┐  │
│  │   React + Vite  │    │      Main Process          │  │
│  │  • 6-Terminal   │◄───│  • PTY Management          │  │
│  │  • Kanban UI    │    │  • API Key Storage         │  │
│  │  • Settings     │    │  • CLI Auto-Install        │  │
│  └─────────────────┘    └────────────────────────────┘  │
│           ▲                        ▲                     │
│           │ IPC                    │ Spawn               │
│           ▼                        ▼                     │
│  ┌──────────────────────────────────────────────────┐   │
│  │      TERMINAL SESSIONS (node-pty + xterm.js)     │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
                            │
                            │ HTTP API (Port 8000)
                            ▼
┌─────────────────────────────────────────────────────────┐
│                    PYTHON BACKEND                        │
│    • Swarm Orchestration    • Git Worktrees             │
│    • Task Queue             • Integrations              │
└─────────────────────────────────────────────────────────┘
```

### Flusso Dati
1. UI React comunica via IPC con Main Process
2. Main Process spawna sessioni PTY per ogni terminale
3. Backend Python gestisce orchestrazione e worktrees
4. Worktrees isolano ogni task in branch separati

---

## Feature Chiave

### 1. Multi-Provider AI Terminal
- **Auto-Install CLI**: Le CLI degli AI si scaricano automaticamente
- Supporto: Claude, Gemini, Codex, OpenCode, Cursor
- Ogni terminale può usare un provider diverso

### 2. 6-Terminal Grid (3x2)
- Visualizzazione simultanea di 6 agents
- Provider separato per terminale
- Task linking: connetti terminali a task Kanban
- Context injection: dettagli task auto-inviati all'AI

### 3. Git Worktree Isolation
```
Task Started → .worktrees/task-XXX created → Agent lavora isolato
                          ↓
              Merge o Discard via Dashboard
```
- Agents lavorano in parallelo senza conflitti
- Main branch protetto
- Facile scartare lavoro fallito

### 4. Secure Settings
- Encryption at rest (Windows DPAPI / macOS Keychain)
- 11 integrazioni: Slack, Discord, Jira, Linear, GitHub + AI providers
- Export to .env per Python backend

---

## Pattern Interessanti

### 1. **Auto-Install Pattern**
CLI che si auto-scaricano al primo uso → zero setup per utente

### 2. **Hybrid Desktop Architecture**
Electron shell + Python backend via HTTP → best of both worlds:
- UI reattiva (React)
- Heavy lifting in Python (orchestrazione, worktrees)

### 3. **Worktree-per-Task**
Isolamento via git worktree invece di branch switching → parallelismo reale

### 4. **Context Injection**
Task details auto-iniettati nel prompt dell'agent → meno context switching umano

### 5. **OS-Level Security**
Uso di DPAPI/Keychain per API keys invece di plaintext config

---

## Pro/Contro

### ✅ Pro
- **Parallelismo vero**: 6 agents simultanei con isolamento git
- **Zero-config**: auto-install delle CLI, onboarding wizard
- **Multi-provider**: non lock-in su un singolo AI
- **Visual management**: Kanban integrato per workflow engineering
- **Security-first**: encryption nativa OS per secrets

### ❌ Contro
- **Solo Windows** (per ora, macOS/Linux coming soon)
- **Overhead Electron**: peso del bundle, RAM usage
- **Dipendenza Python**: richiede backend separato
- **Complessità**: molti layer (Electron + React + Python)
- **No code signing**: SmartScreen warning su Windows

---

## Idee Riutilizzabili

1. **Auto-Install CLI Pattern**
   - Rilevare provider disponibili, scaricare al primo uso
   - Usabile in qualsiasi tool che wrappa CLI esterne

2. **Worktree Orchestration**
   - Pattern per far lavorare più agents sullo stesso repo
   - `.worktrees/task-XXX/` come convenzione

3. **Hybrid Electron + Python**
   - UI veloce in React, logic pesante in Python
   - Comunicazione via HTTP locale

4. **Context Injection for Agents**
   - Arricchire automaticamente i prompt con metadata task
   - Riduce friction nel passaggio di contesto

5. **OS-Level Secret Storage**
   - Usare keychain/credential manager invece di env vars
   - Pattern da adottare per qualsiasi tool con secrets

---

## Note Personali

Squadron risolve un problema reale: coordinare più AI agents su un codebase. L'approccio worktree-per-task è elegante. Il fatto che sia Electron lo rende pesante ma cross-platform.

**Interessante per**: chi vuole gestire swarm di agents locali con visual management.
