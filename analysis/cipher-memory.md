# Byterover Cipher

## Overview
Open-source memory layer specifically designed for coding agents.

## Key Features
- **MCP Integration**: Cursor, Codex, Claude Code, Windsurf, Cline, VS Code, etc.
- **Auto-generate memories** that scale with codebase
- **Cross-IDE memory**: Switch between IDEs without losing context
- **Team sharing**: Real-time memory sharing across dev team
- **Dual Memory Layer**:
  - System 1: Programming concepts, business logic, past interactions
  - System 2: Reasoning steps when generating code

## Built-in Tools (MCP)
- `cipher_extract_and_operate_memory`: ADD/UPDATE/DELETE knowledge
- `cipher_memory_search`: Semantic search
- `cipher_store_reasoning_memory`: Store reasoning traces
- `cipher_workspace_search/store`: Team workspace memory
- Knowledge Graph operations
- `cipher_bash`: Execute commands

## Storage Options
- Vector Store: Qdrant, Milvus, in-memory
- Chat History: PostgreSQL, SQLite

## Relevance for Autoschei
- **CRITICAL**: Exact pattern we need for memogo!
- Dual memory (System 1 + System 2) = what Sergio described
- MCP compatible = integrates with our ecosystem
- Could fork/adapt for memogo integration

## Links
- https://github.com/campfirein/cipher
- https://docs.byterover.dev/cipher/overview
