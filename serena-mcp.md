# Serena MCP - Semantic Code Understanding for AI Agents

**Repository:** https://github.com/oraios/serena
**Company:** Oraios AI (Germany)
**Status:** Open source, active development

## What is Serena?

Serena is a **powerful coding agent toolkit** that provides semantic code retrieval and editing capabilities via MCP (Model Context Protocol). Unlike text-based approaches, it uses **Language Server Protocol (LSP)** to understand code at the symbol level.

Think of it as giving IDE-like capabilities to your LLM/coding agent. Instead of reading entire files and doing grep-like searches, the agent can use code-centric tools like `find_symbol`, `find_referencing_symbols`, and `insert_after_symbol`.

## Key Features

- **Symbol-level code understanding** via LSP integration
- **30+ programming languages** supported (Python, TypeScript, Go, Rust, C#, Java, PHP, etc.)
- **Token efficiency** - dramatically reduces context consumption
- **JetBrains plugin** available for even more robust analysis
- **Memory system** for project-specific knowledge persistence

## Core Tools

| Tool | Description |
|------|-------------|
| `find_symbol` | Global/local symbol search using LSP |
| `find_referencing_symbols` | Find all references to a symbol |
| `get_symbols_overview` | Get top-level symbols in a file |
| `insert_after_symbol` | Insert content after a symbol definition |
| `replace_symbol_body` | Replace entire symbol definition |
| `rename_symbol` | Rename symbol throughout codebase |
| `read_memory` / `write_memory` | Persistent project memory |

## Why This Matters

Traditional coding agents treat code as text:
1. Use `grep` to search
2. Read entire files
3. String replacement for edits

**Problems:**
- No semantic understanding
- High token consumption
- Can't leverage IDE features like "Go to Definition"

**Serena's approach:**
1. Use LSP for symbol-level operations
2. Only load relevant code entities
3. Refactoring-aware edits

## Integration Options

1. **MCP Server** - Works with Claude Code, Claude Desktop, Cursor, VSCode, etc.
2. **JetBrains Plugin** - Leverages JetBrains IDE capabilities
3. **Custom Agents** - Can be integrated into any agent framework
4. **ChatGPT** - Via mcpo OpenAPI bridge

## Quick Start

```bash
# Install via uvx
uvx --from git+https://github.com/oraios/serena serena start-mcp-server --help

# Add to Claude Code
claude mcp add serena-mcp-server "uvx --from git+https://github.com/oraios/serena serena-mcp-server --project $(pwd)"
```

## Architecture

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   LLM/Agent     │────▶│   MCP Server    │────▶│  Language Server│
│ (Claude, etc.)  │◀────│   (Serena)      │◀────│   (LSP)         │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                               │
                               ▼
                        ┌─────────────────┐
                        │  Memory Store   │
                        │ (project-specific)│
                        └─────────────────┘
```

## Related Projects

- **microsoft/multilspy** - Python LSP client library (Serena uses this)
  - https://github.com/microsoft/multilspy
  - NeurIPS 2023 paper: "Monitor-Guided Decoding of Code LMs with Static Analysis"

- **Agno** - Agent OS for production AI APIs
  - https://docs.agno.com/agent-os/introduction
  - Can run Serena as part of a larger agent system

## Community Feedback

Reddit discussions report significant improvements:
- Reduced token consumption
- Better code understanding in large projects  
- More accurate refactoring operations

## Resources

### Official
- Docs: https://oraios.github.io/serena/
- Tools list: https://oraios.github.io/serena/01-about/035_tools.html
- Language support: https://oraios.github.io/serena/01-about/020_programming-languages.html
- Workflow guide: https://oraios.github.io/serena/02-usage/040_workflow.html
- JetBrains plugin: https://oraios.github.io/serena/02-usage/025_jetbrains_plugin.html

### Custom Integration
- Custom agent guide: https://github.com/oraios/serena/blob/main/docs/03-special-guides/custom_agent.md
- ChatGPT integration: https://github.com/oraios/serena/blob/main/docs/03-special-guides/serena_on_chatgpt.md

### Articles & Analysis
- Architecture deep-dive: https://medium.com/@souradip1000/deconstructing-serenas-mcp-powered-semantic-code-understanding-architecture-75802515d116
- Japanese analysis: https://blog.lai.so/serena/
- Claude Code enhancement: https://robertmarshall.dev/blog/turning-claude-code-into-a-development-powerhouse/

### Related MCP Resources
- OpenWebUI MCP: https://docs.openwebui.com/openapi-servers/mcp
- Jan MCP: https://www.jan.ai/docs/desktop/mcp-examples/browser/browserbase#enable-mcp

### Reddit Discussions
- https://www.reddit.com/r/ClaudeAI/comments/1lfsdll/try_out_serena_mcp_thank_me_later/
- https://www.reddit.com/r/ClaudeCode/comments/1mguoia/absolutely_insane_improvement_of_claude_code/

## Key Insight for CodyGody

Serena demonstrates that **semantic code understanding via LSP** is the next evolution for coding agents. Key patterns to adopt:

1. **Symbol-centric operations** instead of text-based
2. **Language server integration** for multi-language support
3. **Memory persistence** for project context
4. **Efficient retrieval** - only load what's needed

This could dramatically improve token efficiency and code quality in CodyGody's implementation.

---

*Added: 2026-02-08*
*Source: Sergio via WhatsApp*
