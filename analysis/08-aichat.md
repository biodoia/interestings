# AIChat

**URL:** https://github.com/sigoden/aichat

## Overview
All-in-one LLM CLI tool: Shell Assistant, Chat-REPL, RAG, AI Tools & Agents

## Stack
- **Rust** (cargo install aichat)
- Cross-platform (macOS, Linux, Windows, Android Termux)

## Providers (20+)
OpenAI, Claude, Gemini, Ollama, Groq, Azure-OpenAI, VertexAI, Bedrock, 
Github Models, Mistral, Deepseek, AI21, XAI Grok, Cohere, Perplexity, 
Cloudflare, OpenRouter, Ernie, Qianwen, Moonshot, ZhipuAI, MiniMax, 
Deepinfra, VoyageAI + any OpenAI-Compatible

## Feature Chiave
1. **Shell Assistant** — NL → shell commands (OS-aware)
2. **CMD Mode** — one-shot queries
3. **REPL Mode** — interactive chat with tab completion, history
4. **Multi-form Input** — stdin, files, dirs, URLs, `backtick commands`
5. **Roles** — custom prompts per tailor behavior
6. **Sessions** — context-aware conversations
7. **Macros** — combine REPL commands
8. **RAG** — external document integration
9. **Function Calling** — AI Tools + MCP support

## Pattern Interessanti
1. **Unified interface** per 20+ providers
2. **Multi-input types** con sintassi uniforme (-f file, .file in REPL)
3. **Role = prompt + model config**
4. **Session persistence** per continuità
5. **Macro system** per automazione

## Pro
- Rust = veloce, single binary
- Providers massivi out of the box
- RAG built-in
- MCP support
- Termux support (Android!)

## Contro
- Non specifico per coding (general purpose)
- No git integration nativa

## Idee Riutilizzabili per CodyGody
- Multi-provider architecture unificata
- Role + Session system
- Multi-form input handling
- Macro system per workflow
- MCP integration
