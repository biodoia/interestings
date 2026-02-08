# Cloi

**URL:** https://github.com/gabrielchasukjin/cloi

## Overview
Local debugging agent che gira nel terminale. Privacy-first.

## Stack
- Node.js CLI (npm install -g @cloi-ai/cloi)
- Python per RAG (CodeBERT)
- GPL-3.0

## Feature Chiave
1. **On-device models** — Ollama (Phi-4, Qwen3, etc.) o Claude API
2. **RAG system** — CodeBERT embeddings + BM25 keyword search
3. **Safe changes** — review diff prima di applicare
4. **Terminal logging** — cattura output in ~/.cloi/terminal_output.log
5. **Zero setup** — auto-installa CodeBERT (~500MB), FAISS, dependencies
6. **Structured outputs** — JSON-based patches

## Commands
- `/debug` — auto-fix errori con RAG
- `/index` — re-index codebase
- `/model` — switch tra modelli
- `/logging` — setup error logging (zsh)

## Pattern Interessanti
1. **Hybrid RAG** — CodeBERT semantic + BM25 keyword = migliore retrieval
2. **Background service** — CodeBERT su porta 3090 per embeddings veloci
3. **Terminal capture** — log rotation automatica (1MB)
4. **Diff review** — mai applica senza conferma

## Pro
- Privacy totale (local-first)
- RAG automatico
- Zero config
- Works with existing Ollama

## Contro
- Beta, experimental
- macOS only (testato su M2/M3)
- zsh-centric
- Richiede 8GB+ RAM, 10GB+ storage

## Idee Riutilizzabili
- Hybrid RAG (semantic + keyword)
- Terminal output capture per error context
- Auto-download models on first use
