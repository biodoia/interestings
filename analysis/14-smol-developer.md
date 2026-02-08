# smol developer

**URL:** https://github.com/smol-ai/developer

## Overview
First library to embed a developer agent in your own app. "Junior developer" agent.

## Stack
- Python (pip install smol_dev)
- Poetry
- Agent Protocol API

## Concept
Human-centric, coherent whole program synthesis. "create-anything-app"

## 3 Modes
1. **Git Repo mode** — CLI, human-in-the-loop iteration
2. **Library mode** — import and use in your app
3. **API mode** — Agent Protocol standard REST API

## Core Pipeline
```python
from smol_dev.prompts import plan, specify_file_paths, generate_code_sync

shared_deps = plan(prompt)                              # 1. coding plan
file_paths = specify_file_paths(prompt, shared_deps)    # 2. file list (JSON via Function Calling)
for fp in file_paths:
    code = generate_code_sync(prompt, shared_deps, fp)  # 3. generate each file
```

## Workflow (Human-in-the-loop)
1. Human writes basic prompt
2. AI generates code
3. Human runs/reads code
4. Human adds to prompt (underspecified parts, errors)
5. Loop until happy
6. Take over codebase when AI gets in the way

## Pattern Interessanti
1. **Library-first** — designed to be imported, not just CLI
2. **Agent Protocol** — standard API per interoperability
3. **Shared deps** — coding plan shared tra file generation
4. **Human takeover** — graceful handoff when AI fails
5. **debugger.py** — reads whole codebase per error fixes
6. **Function Calling for JSON** — guaranteed file paths format

## Philosophy
"Engineering with prompts, not prompt engineering"
- Prompts as iterative specs
- Human stays in control
- AI as junior dev, not replacement

## Pro
- Embeddable (library mode)
- Agent Protocol standard
- Simple mental model
- Human-centric

## Contro
- Full generation (not incremental)
- Basic compared to modern tools
- Limited context management

## Idee Riutilizzabili
- Library-first design (importable)
- Agent Protocol for API
- plan → file_paths → generate pipeline
- Shared dependencies concept
- Human takeover philosophy
