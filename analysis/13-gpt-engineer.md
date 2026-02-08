# gpt-engineer

**URL:** https://github.com/AntonOsika/gpt-engineer

## Overview
L'OG code generation platform. Precursore di lovable.dev. 52K+ stars.

## Stack
- Python (pip install gpt-engineer)
- Poetry per dev
- MIT-like license

## Providers
OpenAI, Azure OpenAI, Anthropic, local models (WizardCoder, etc.)

## Concept
```
prompt file (natural language) → AI generates full codebase → execute
```

## Feature Chiave
1. **Full codebase generation** — da prompt a progetto completo
2. **Improve mode** — `gpte -i` per iterare su codice esistente
3. **Vision support** — input immagini (diagrams, mockups)
4. **Custom preprompts** — identity agent persistente tra progetti
5. **Benchmarking** — `bench` CLI per testare agents su APPS, MBPP
6. **Docker support** — containerized execution

## Usage
```bash
# Create prompt file in project folder
echo "Create a snake game in Python" > projects/snake/prompt

# Generate
gpte projects/snake

# Improve existing
gpte projects/snake -i

# With vision
gpte projects/ui --image_directory prompt/images
```

## Pattern Interessanti
1. **Prompt file convention** — file `prompt` (no extension) in folder
2. **Preprompts override** — custom identity persistente
3. **Vision for context** — diagrams/mockups come input
4. **Benchmarking built-in** — test agents su dataset pubblici
5. **Commercial evolution** — lovable.dev come SaaS version

## Pro
- Battle-tested (52K+ stars)
- Simple mental model
- Vision support
- Benchmarking tools

## Contro
- Meno attivo (raccomandano Aider per CLI moderna)
- Full generation vs incremental editing
- No RAG/context sophisticato

## Idee Riutilizzabili
- Prompt file convention
- Preprompts per agent identity
- Vision input per UI/diagrams
- Built-in benchmarking system
