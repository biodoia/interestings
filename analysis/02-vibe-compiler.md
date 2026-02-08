# Vibe Compiler (vibec)

**URL:** https://github.com/Strawberry-Computer/vibe-compiler  
**Licenza:** MIT  
**Stato:** Attivo

---

## Overview

vibec è un **compilatore self-compiling** che trasforma "prompt stacks" (markdown) in codice e test usando LLM generation. La cosa unica: **può compilare se stesso** attraverso un processo di bootstrap, evolvendo la propria implementazione attraverso stage numerati.

Il concetto core: **il compilatore evolve durante la compilazione**.

---

## Stack Tecnologico

| Component | Tecnologia |
|-----------|------------|
| **Runtime** | Node.js |
| **LLM API** | OpenAI-compatible (OpenRouter default) |
| **Default Model** | Claude 3.7 Sonnet |
| **Prompt Format** | Markdown custom |
| **Test Framework** | tape |
| **Config** | JSON (vibec.json) |

---

## Architettura

```
stacks/
├── core/              # Prompt stacks per funzionalità core
│   ├── 001_add_logging.md
│   ├── 002_add_plugins.md
│   └── plugins/       # Static/dynamic plugins
└── tests/             # Prompt stacks per test generation

              ↓ vibec processa ↓

output/
├── bootstrap/         # Output bootstrap iniziale
├── current/           # Latest merged version (runtime)
└── stacks/            # Staged outputs (per git history)
    ├── core/
    │   ├── 001_add_logging/
    │   ├── 002_add_plugins/
    └── tests/
```

### Flusso di Compilazione

1. **Inizio**: parte da `bin/vibec.js` (implementazione iniziale)
2. **Stage Sequenziali**: processa 001, 002, 003...
3. **Self-Update**: quando uno stage genera nuovo `vibec.js`, usa quello per stage successivi
4. **Output Merging**: "Last-Wins" strategy per aggregare in `output/current/`

---

## Feature Chiave

### 1. Self-Compiling Bootstrap
Il compilatore può **evolvere se stesso**:
- Stage 001 aggiunge logging
- Stage 002 aggiunge plugins
- Stage 003 aggiunge CLI
- Ogni stage usa la versione precedente per compilarsi

### 2. Prompt Structure (Markdown)
```markdown
# Component Name

Description of the generation task.

## Context: file1.js, file2.js
## Output: path/to/output.js
```
- `## Context:` - file da includere come contesto
- `## Output:` - path output (multipli supportati)

### 3. Plugin System

**Static Plugins (.md)**
- Appesi ai prompt in ordine alfabetico
- Per aggiungere constraints/context riutilizzabili

**Dynamic Plugins (.js)**
- Eseguiti come async functions
- Accesso a: config, stack, promptNumber, testResult
- Timeout configurabile

### 4. Iteration System (Self-Healing)
```
Test fails → Capture output → Re-run prompt with test output
         ↓
Repeat up to N iterations → Fix automatically
```

### 5. Staged Outputs per Git History
Ogni stage produce output in cartella separata → tracciabilità completa delle evoluzioni

---

## Pattern Interessanti

### 1. **Self-Compiling Pattern**
Il tool evolve durante l'uso. Ogni feature aggiunta diventa disponibile per feature successive.

### 2. **Prompt-as-Code**
I prompt markdown SONO il codice sorgente. Il LLM è il compilatore.

### 3. **Context Injection via Markdown Headers**
`## Context: file.js` → elegante, leggibile, declarativo

### 4. **Iteration/Self-Healing**
Test falliti → ri-esegui con output errore → lascia che LLM corregga

### 5. **Plugin Prompts**
Esempio brillante: plugin che forza LLM a commentare il codice con snippet del prompt che l'ha generato:
```markdown
// PROMPT: <relevant prompt snippet>
```
→ Tracciabilità prompt → codice

### 6. **Last-Wins Merge**
Strategia semplice per aggregare output di stage multipli

---

## Pro/Contro

### ✅ Pro
- **Concetto innovativo**: prompt stacks come sorgente, LLM come compilatore
- **Self-improving**: il tool migliora se stesso
- **Tracciabilità**: staged outputs mantengono history
- **Flessibile**: qualsiasi LLM OpenAI-compatible
- **Iteration system**: auto-fix dei test failures
- **Plugin system**: estendibile con MD e JS

### ❌ Contro
- **Dipendenza LLM**: qualità output dipende dal modello
- **Costi API**: ogni compilazione = chiamate API
- **Debugging complesso**: quando il LLM sbaglia, debug non banale
- **Non deterministico**: stesso prompt può dare output diversi
- **Learning curve**: capire il flusso bootstrap richiede tempo

---

## Idee Riutilizzabili

1. **Prompt-as-Source Pattern**
   - Usare markdown strutturato come input per generazione codice
   - `## Context:` e `## Output:` come direttive

2. **Self-Healing Iteration**
   - Test fails → re-prompt con errore → retry
   - Applicabile a qualsiasi pipeline LLM-based

3. **Traceability Comments**
   - Forzare LLM a commentare con snippet prompt
   - Utile per debug e audit

4. **Staged Output Pattern**
   - Ogni step in cartella separata
   - `output/stacks/001_xxx/`, `002_xxx/`
   - Git-friendly, rollback facile

5. **Plugin Injection Pattern**
   - Plugins come markdown appesi al prompt
   - Zero overhead, massima flessibilità

6. **Bootstrap Evolution**
   - Tool che evolve durante il suo stesso uso
   - Pattern per meta-tools

---

## Esempio Pratico: Pong Game

Il README include un tutorial per creare un gioco Pong:

```markdown
# Pong Game Initial Setup

Generate a simple Pong game using HTML, CSS, and JavaScript:

- Use `<canvas width="800" height="400" id="pongCanvas">`
- Draw a white paddle...
- Draw a white ball...

## Output: index.html
## Output: styles.css
## Output: game.js
```

Poi aggiungi scoring, poi AI player → ogni step è un prompt che evolve il gioco.

---

## Note Personali

vibec è un esperimento affascinante di "meta-programmazione LLM". L'idea di prompt stacks che compilano se stessi è elegante. Il pattern di self-healing via iteration è pratico e riutilizzabile.

**Interessante per**: chi vuole esplorare LLM-as-compiler, generazione codice strutturata, o pipeline di prompt concatenati.
