# Maestro Analysis 🎼

> Local AI code review assistant built on DSPy-Go (26 ⭐)
> https://github.com/XiaoConstantine/maestro
> **Language: Go** ✅ | **Framework: DSPy-Go + Bubbletea**

## Overview

Maestro è il tool più avanzato della lista. Combina:
- **DSPy-Go** per orchestrazione LLM
- **Bubbletea v2** per TUI
- **AST parsing** per semantic analysis
- **Vector search** per code similarity

27,000+ linee di codice, architettura production-grade.

## Architettura

```
┌─────────────────────────────────────────────────────────────────────┐
│ USER INTERFACE                                                      │
│ ┌─────────────┐ ┌─────────────────────────┐ ┌────────────────────┐  │
│ │ CLI Mode    │ │ TUI v2 (Bubbletea)      │ │ GitHub API         │  │
│ │ • Spinner   │ │ • Vim Keybindings       │ │ • PR Changes       │  │
│ │ • Progress  │ │ • Command Palette       │ │ • Review Comments  │  │
│ └─────────────┘ │ • File Tree / TODOs     │ │ • OAuth2           │  │
│                 │ • Review Display        │ └────────────────────┘  │
│                 └─────────────────────────┘                         │
└─────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│ MAESTRO SERVICE (Singleton)                                         │
│ ┌─────────────────────────────────────────────────────────────────┐ │
│ │ AgentPool (Persistent)                                          │ │
│ │ ┌─────────────────┐ ┌─────────────────────────────────────────┐ │ │
│ │ │ PRReviewAgent   │ │ UnifiedReActAgent (QA)                  │ │ │
│ │ └─────────────────┘ └─────────────────────────────────────────┘ │ │
│ │ ┌─────────────────┐ ┌─────────────────────────────────────────┐ │ │
│ │ │ ClaudeProcessor │ │ GeminiProcessor                         │ │ │
│ │ │ (Sonnet 4.5)    │ │ (Gemini 3 Pro Preview)                  │ │ │
│ │ └─────────────────┘ └─────────────────────────────────────────┘ │ │
│ └─────────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────┘
                              │
          ┌───────────────────┼───────────────────┐
          ▼                   ▼                   ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ REVIEW ENGINE   │ │ UNIFIED REACT   │ │ SEARCH ENGINE   │
│ • Chunker       │ │ AGENT           │ │ • Semantic      │
│ • Workflow      │ │ • Tool Select   │ │ • Hybrid Match  │
│ • 120 Workers   │ │ • Context Mgmt  │ │ • Code Index    │
└─────────────────┘ └─────────────────┘ └─────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│ DATA LAYER                                                          │
│ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────────────┐ │
│ │ SQLite +        │ │ Embedding       │ │ Shared Memory           │ │
│ │ sqlite-vec      │ │ Router          │ │ (InMemory/SQLite)       │ │
│ └─────────────────┘ └─────────────────┘ └─────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────┘
```

## Core Features

### 1. AST-Based Context Analysis
```go
// Parsing Go code structure
- Packages, imports, types, functions
- 15+ lines surrounding context
- Semantic purpose detection
- Dependency tracking
```

### 2. Multi-Stage Review Pipeline
```
Context Preparation → Analysis → Validation → Aggregation
       │                 │           │            │
       ▼                 ▼           ▼            ▼
   AST Parse        LLM Call    Dedup Engine   File Groups
```

### 3. TUI v2 (Bubbletea)
- Vim keybindings (Normal, Insert, Visual, Command, Search modes)
- Command palette con fuzzy search
- File tree explorer
- TODO tracking
- Split-pane layout

### 4. Semantic Code Search (Sgrep)
- Vector embeddings locali (nomic-embed-text, 768 dims)
- Hybrid search: semantic + keyword
- Guideline discovery
- ReAct agent integration

### 5. Multi-Model Support
```bash
# LLaMA.cpp locale
./maestro --model="llamacpp:" --pr=123

# Ollama
./maestro --model="ollama:codellama" --pr=123

# Claude
./maestro --model="anthropic:claude-3-sonnet" --pr=123

# Gemini
./maestro --model="google:gemini-pro" --pr=123
```

## TUI Commands

| Comando | Descrizione |
|---------|-------------|
| `/review <PR>` | Review PR |
| `/ask <question>` | Q&A con ReAct agent |
| `/claude <prompt>` | Claude Sonnet 4.5 |
| `/gemini <prompt>` | Gemini 3 Pro Preview |
| `/clear` | Clear history |

## Vim Keybindings

| Key | Action |
|-----|--------|
| `h/j/k/l` | Navigate |
| `i` | Insert mode |
| `v` | Visual mode |
| `:` | Command mode |
| `/` | Search |
| `ctrl+b` | Toggle file tree |
| `ctrl+t` | Toggle TODO panel |

## Cosa Copiare per GoView

### Must-Have
1. **Bubbletea v2** - TUI framework (già usiamo lipgloss)
2. **Multi-model** - pattern per switch provider
3. **Vim keybindings** - UX pro
4. **Command palette** - fuzzy search comandi

### Nice-to-Have
1. **DSPy-Go** - orchestrazione LLM strutturata
2. **sqlite-vec** - vector search locale
3. **ReAct agent** - reasoning iterativo
4. **AST parsing** - context semantico

### Architecture Patterns
1. **Singleton Service** - MaestroService
2. **Agent Pool** - persistent agents
3. **Request Router** - `/review`, `/ask`, `/claude`
4. **Shared Memory** - context cross-request

## Relevanza per Gommander

**Altissima** - Maestro è esattamente quello che vogliamo:

| Feature | Maestro | GoView (attuale) | GoView (target) |
|---------|---------|------------------|-----------------|
| Language | Go | Go | Go |
| TUI | Bubbletea v2 | lipgloss | Bubbletea v2 |
| Multi-model | ✅ | ✅ | ✅ |
| Local LLM | ✅ (Ollama/llama.cpp) | ✅ (Ollama) | ✅ |
| Vector search | ✅ | ❌ | ❓ |
| AST parsing | ✅ | ❌ | ❓ |
| Vim keys | ✅ | ❌ | ✅ |
| ReAct agent | ✅ | ❌ | ❓ |

## DSPy-Go Integration

```go
// Esempio pattern DSPy-Go
import "github.com/XiaoConstantine/dspy-go"

// Structured LLM calls
signature := dspy.Signature{
    Inputs:  []string{"code_chunk", "context"},
    Outputs: []string{"issues", "suggestions"},
}

module := dspy.ChainOfThought(signature)
result := module.Forward(inputs)
```

## Setup Locale

```bash
# One-time: install llama.cpp + models
make setup

# Start embedding + LLM servers
make local

# Runs:
# - Embedding server (port 8080) - nomic-embed-text
# - LLM server (port 8081) - Qwen3-1.7B
```

## Conclusione

Maestro è il gold standard per AI code review in Go.
Dobbiamo studiare:
1. Architettura agent pool
2. DSPy-Go patterns
3. Bubbletea v2 TUI
4. Vector search integration
