# Vibe Coding Tools - Analisi URL Pendenti 🛠️

> 12 tool analizzati in dettaglio
> Ultimo aggiornamento: 2026-02-09

---

## 07. Rulebook-AI
**URL:** https://github.com/botingw/rulebook-ai
**Focus:** AI Environment Manager

### Descrizione
CLI per packaging e deploy di "AI environments" (rules, context, tools) a coding assistants.

### Funzionalità Chiave
- **Portable Environments**: Define una volta, deploy ovunque
- **Pack System**: Ambienti versionabili e componibili
- **Multi-assistant**: Cursor, Windsurf, Cline, RooCode, Claude Code, Gemini CLI, Codex CLI
- **Memory Bank**: Context persistente (`memory/`, `tools/`)

### Comandi
```bash
uvx rulebook-ai packs add light-spec
uvx rulebook-ai project sync
uvx rulebook-ai project sync --assistant cursor copilot
```

### Relevanza per Gommander: ⭐⭐⭐⭐
Pattern **environment portability** interessante per config management.

---

## 08. AIChat
**URL:** https://github.com/sigoden/aichat
**Focus:** All-in-one LLM CLI

### Descrizione
CLI completo con Shell Assistant, Chat-REPL, RAG, AI Tools & Agents.

### Funzionalità Chiave
- **20+ Providers**: OpenAI, Claude, Gemini, Ollama, Groq, Deepseek, Qwen...
- **Shell Assistant**: Natural language → shell commands
- **RAG built-in**: Retrieval Augmented Generation
- **Multi-form input**: stdin, files, directories, URLs
- **Sessions**: Context-aware conversations
- **Macros**: Automate repetitive REPL commands
- **Rust-based** 🦀

### Comandi
```bash
aichat hello                    # CMD mode
aichat -f image.png -f data.txt # Multi-file input
aichat -f '`git diff`'          # External commands
```

### Relevanza per Gommander: ⭐⭐⭐⭐⭐
**GOLD STANDARD** per CLI LLM. Rust, multi-provider, RAG, Shell Assistant.

---

## 09. Cloi
**URL:** https://github.com/gabrielchasukjin/cloi
**Focus:** Local Debugging Agent

### Descrizione
Debugging agent locale che gira nel terminale.

### Funzionalità Chiave
- **RAG System**: CodeBERT + BM25 hybrid search
- **On-device models**: Ollama + Anthropic Claude
- **Terminal logging**: Auto-capture errors (zsh)
- **Zero setup**: RAG auto-install on first `/debug`
- **Privacy-first**: Tutto locale

### Comandi REPL
```
/debug   # Auto-fix errors con RAG
/index   # Re-index codebase
/model   # Cambia model
/logging # Setup error logging
```

### Requisiti
- 8GB RAM min (16GB+ recommended)
- macOS Big Sur 11.0+
- Ollama auto-installed

### Relevanza per Gommander: ⭐⭐⭐⭐
Pattern **RAG hybrid search** (CodeBERT + BM25), debugging-focused.

---

## 10. Codai
**URL:** https://github.com/meysamhadeli/codai
**Focus:** AI Coding Agent for Terminal
**Language: Go** ✅

### Descrizione
Coding agent in Go con context awareness via Tree-sitter.

### Funzionalità Chiave
- **Multi-provider**: OpenAI, Anthropic, Gemini, Grok, DeepSeek, Qwen
- **Tree-sitter summarization**: Full project context
- **Multi-file editing**: Modifica più file simultaneamente
- **Token tracking**: Usage e costi per request
- **Config file**: `codai-config.yml`
- **.codai-gitignore**: Exclude files

### Uso
```bash
go install github.com/meysamhadeli/codai@latest
export API_KEY="your_api_key"
codai code
```

### Relevanza per Gommander: ⭐⭐⭐⭐⭐
**Go-based**, Tree-sitter, multi-provider. Pattern simile a goview!

---

## 11. MyCoder
**URL:** https://github.com/drivecore/mycoder
**Focus:** AI-Powered Coding Tasks

### Descrizione
CLI per task di coding con Anthropic Claude, OpenAI, Ollama.

### Funzionalità Chiave
- **Parallel sub-agents**: Concurrent task processing
- **Self-modification**: Può modificare il proprio codice
- **GitHub Integration**: Issues/PRs automation
- **MCP Support**: Model Context Protocol
- **Message compaction**: Context window management
- **Browser automation**: Playwright integration
- **Interactive corrections**: Ctrl+M per correzioni real-time

### Config
```javascript
// mycoder.config.js
export default {
  provider: 'anthropic',
  model: 'claude-3-7-sonnet-20250219',
  githubMode: true,
  mcp: { servers: [...] }
}
```

### GitHub Comment Commands
```
/mycoder implement a PR for this issue
/mycoder create an implementation plan
```

### Relevanza per Gommander: ⭐⭐⭐⭐
Pattern **parallel agents**, **MCP support**, **GitHub integration**.

---

## 12. AIAssist
**URL:** https://github.com/mehdihadeli/AIAssist
**Focus:** Context-Aware AI Coding Assistant
**Language: .NET/C#**

### Descrizione
CLI per code development con RAG o Tree-sitter summarization.

### Funzionalità Chiave
- **Two strategies**: 
  - Embedding/RAG based
  - Tree-sitter summarization
- **Multi-provider**: OpenAI, Azure, Ollama, Anthropic, OpenRouter, Grok, Gemini, DeepSeek, Qwen
- **Output formats**: Unified Diff, Code Block, Search-Replace
- **Token tracking**: Usage e pricing
- **Syntax highlighting**: Themes (dracula, vscode light)
- **.aiassistignore**: Custom excludes

### Comandi
```bash
dotnet tool install --global AIAssist
aiassist code    # Code assistant
aiassist chat    # Chat mode
aiassist explain # Explain code
```

### Relevanza per Gommander: ⭐⭐⭐⭐
Pattern **dual context strategy** (RAG vs Tree-sitter).

---

## 13. GPT-Engineer
**URL:** https://github.com/AntonOsika/gpt-engineer
**Stars:** 50k+ (legendary)
**Focus:** Codegen Experimentation Platform

### Descrizione
OG code generation. Precursore di Lovable.dev.

### Funzionalità Chiave
- **Prompt → Code**: Specifica in natural language
- **Iterative improvement**: Loop human-in-the-loop
- **Preprompts customization**: Override identity
- **Vision support**: Image input per UX diagrams
- **Benchmarking**: APPS, MBPP datasets

### Uso
```bash
gpte projects/my-new-project
gpte projects/my-old-project -i  # Improve existing
```

### Note
- Ora raccomanda **aider** per CLI hackable
- **Lovable.dev** è l'evoluzione managed

### Relevanza per Gommander: ⭐⭐⭐
Pattern storico, ma **aider** è più attuale.

---

## 14. Smol Developer
**URL:** https://github.com/smol-ai/developer
**Focus:** Embeddable Developer Agent

### Descrizione
"Junior developer" che scaffolda codebase intere.

### Funzionalità Chiave
- **Create-anything-app**: No specific starters
- **Library mode**: Importabile in altri progetti
- **Agent Protocol API**: REST API per automazione
- **Human-in-the-loop**: Iterative refinement

### Modi
```python
# Library mode
from smol_dev.prompts import plan, specify_file_paths, generate_code_sync
shared_deps = plan(prompt)
file_paths = specify_file_paths(prompt, shared_deps)

# API mode
poetry run api  # Starts Agent Protocol server
```

### Relevanza per Gommander: ⭐⭐⭐
Pattern **embeddable agent**, **Agent Protocol**.

---

## 15. CompilerBrain
**URL:** https://github.com/Cysharp/CompilerBrain
**Focus:** C# Expert CLI Agent
**Language: C#**

### Descrizione
CLI coding agent specifico per C#, opera contro Roslyn compiler.

### Funzionalità Chiave (in sviluppo)
- **In-memory compilation**: Roslyn integration
- **Immutable additions**: Fast diagnostics senza sporcare files
- **Parallel sub-agents**: No git worktree needed
- **Semantic editing**: Minimal scope operations
- **C# Expert prompt**: Rich context per C# devs

### Pattern Unico
```
Parse solution → In-memory compile → SyntaxTree analysis → Symbol search → Semantic edit
```

### Relevanza per Gommander: ⭐⭐⭐⭐
Pattern **compiler integration** interessante per linguaggi con LSP/compiler API.

---

## 16. VibEx-CLI
**URL:** https://github.com/Gymnott1/VibeEx-CLI
**Focus:** Code Preparation for AI

### Descrizione
CLI per preparare codice per AI assistants, rimuovendo noise e secrets.

### Funzionalità Chiave
- **Combine files**: Single document per AI
- **Remove comments**: Reduce token usage
- **Scrub secrets**: API keys, tokens, personal data
- **Monitor mode**: Auto-update on file changes
- **Trim/Cut**: Character ranges inclusion/exclusion
- **.vibesafeignore**: Custom excludes

### Comandi
```bash
vx c                      # Combine all
vx c --rc --rp            # Remove comments + private
vx c -mx                  # Monitor mode
vx c --trim="s-200"       # Only first 200 chars
```

### Output
`vx_{folder_name}.txt` - single file per AI.

### Relevanza per Gommander: ⭐⭐⭐
Pattern **context preparation** per AI. Complementare a crev.

---

## 17. VibeSafe
**URL:** https://github.com/slowcoder360/vibesafe
**Focus:** AI-Native DevSecOps CLI

### Descrizione
Security scanner per vibe coding. Detecta vulnerabilità prima del deploy.

### Funzionalità Chiave
- **Secret scanning**: AWS keys, JWTs, SSH keys, .env
- **Dependency CVE check**: OSV.dev integration
- **Insecure config detection**: DEBUG=true, devMode, CORS
- **HTTP client scan**: Missing timeouts
- **Upload validation**: File size/type checks
- **Exposed endpoints**: /admin, /debug, /metrics
- **Rate limiting check**: Heuristic analysis
- **vibesafe install**: Anti-typosquatting package install

### Comandi
```bash
vibesafe scan
vibesafe scan -r ai-report.md   # AI-powered report
vibesafe scan --high-only        # Critical only
vibesafe install express         # Safe npm install
vibesafe install pkg -- --save-dev
```

### AI Report
Con OpenAI API key, genera fix suggestions.

### Relevanza per Gommander: ⭐⭐⭐⭐
Pattern **security scanning**, **safe package install** (anti-slopsquatting).

---

## 📊 Riassunto Categorie

### AI Coding Agents (Code Generation)
| Tool | Language | Key Feature |
|------|----------|-------------|
| Codai | **Go** ✅ | Tree-sitter, multi-provider |
| AIAssist | C# | RAG + Tree-sitter dual |
| MyCoder | Node.js | Parallel agents, MCP |
| GPT-Engineer | Python | OG codegen |
| Smol Developer | Python | Embeddable agent |

### CLI LLM Tools
| Tool | Language | Key Feature |
|------|----------|-------------|
| AIChat | **Rust** ✅ | All-in-one, 20+ providers |
| Cloi | Node.js | RAG debugging |

### Security & Preparation
| Tool | Focus |
|------|-------|
| VibeSafe | DevSecOps, CVE, secrets |
| VibEx-CLI | Context prep, noise removal |

### Environment Management
| Tool | Focus |
|------|-------|
| Rulebook-AI | AI env portability |

### Language-Specific
| Tool | Language | Focus |
|------|----------|-------|
| CompilerBrain | C# | Roslyn integration |

---

## 🎯 Top 5 per Gommander

1. **AIChat** (Rust) - All-in-one CLI reference
2. **Codai** (Go) - Tree-sitter, stesso stack
3. **MyCoder** - Parallel agents, MCP
4. **VibeSafe** - Security integration
5. **Cloi** - RAG debugging pattern
