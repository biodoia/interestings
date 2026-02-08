# CompilerBrain

**URL:** https://github.com/Cysharp/CompilerBrain

## Overview
CLI Coding Agent "not for vibe-coding, for C# Expert". Compiler-native approach.

## Stack
- .NET / C#
- Roslyn (C# Compiler)
- Cysharp (creators of UniTask, MessagePack, etc.)

## Status
🚧 Under development — watch for release

## Concept Unico
Invece di operazioni file-based (grep, build), opera direttamente contro il compilatore Roslyn.

## Feature Chiave
1. **In-memory compilation** — no file dirtying
2. **Immutable compilation** — modifiche come addizioni, non mutazioni
3. **Parallel sub-agents** — tutto in-memory, no git worktree richiesto
4. **SyntaxTree search** — fast search su AST in-memory
5. **Symbol analysis** — semantic navigation
6. **Minimal scope edits** — semantics-aware, risparmia tokens
7. **C# specialized prompts** — rich context per C# developers

## Pattern Interessanti
1. **Compiler-as-backend** — invece di file system
2. **Immutable model** — functional approach alle modifiche
3. **In-memory parallelism** — no filesystem contention
4. **Semantic editing** — opera su AST, non su text
5. **Language-specific** — specializzato vs general purpose

## Differenze vs General Agents
| General Agent | CompilerBrain |
|--------------|---------------|
| File-based ops | Compiler-based ops |
| grep/sed | SyntaxTree search |
| git worktree | In-memory branches |
| Text editing | Semantic editing |
| Any language | C# specialized |

## Pro
- Compiler accuracy (no hallucinated syntax)
- Fast parallel execution
- Semantic awareness
- Token efficient (minimal scopes)

## Contro
- C# only
- Still in development
- Requires Roslyn knowledge

## Idee Riutilizzabili
- Compiler-native approach per linguaggi specifici
- In-memory compilation per parallelism
- Immutable modification model
- Language-specific expert agents
- Semantic (AST) vs textual editing
