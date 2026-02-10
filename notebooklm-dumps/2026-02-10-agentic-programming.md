# NotebookLM Dump - Programmazione Agentica Enterprise
> Importato: 2026-02-10 12:17

## Topics Covered
1. Bug Bounty Platforms
2. Analogie AI/Sogni
3. Programmazione Agentica Enterprise (2025-2026)
4. Tecnica Ralph Wiggum
5. AGENTS.md (Contesto Passivo)

---

## 🎯 Key Takeaways

### Bug Bounty Platforms
- **Global Leaders**: HackerOne, Bugcrowd, Synack (1-2 weeks payout)
- **EU Fast**: YesWeHack (5 days), Intigriti (5-7 days)
- **Web3**: Immunefi, Code4rena, Hackenproof (2-5 days, crypto)
- **Big Tech Direct**: Microsoft, Google, Meta, Apple, Amazon

### Analogie AI/Sogni
- LLM inference ≈ dreaming (pattern generation without validation)
- Text instability in AI images ≈ text in dreams
- "Lucid Dream" validation model for hallucination correction
- ReAct 3.0: "cognitive heartbeat" during idle (DMN simulation)

### Dal Vibe Coding al Professionale
- **2025 shift**: 20% AI assist → 80-100% agent-driven coding
- **Vibe Coding** = superficial generation based on vibes
- **Automatic Programming** = high-quality SW following human vision
- **Comprehension Debt**: +91% review time, risk of "rubber stamp"

### Enterprise Challenges
- **Context Collapse**: 40% → 7% productivity in legacy codebases
- **The 80% Problem**: Errors evolved from syntactic to conceptual
- **Sycophantic agents**: Never challenge wrong premises

### Tecnica Ralph Wiggum
Loop continuo:
1. **Select** next task from prd.json
2. **Implement** code changes
3. **Validate** (tests, type checks)
4. **Commit** if passed
5. **Update state** + log learnings
6. **Reset context** completely

**Why it works**: Stateless-but-iterative, avoids confusion accumulation

**4 persistent memory channels**:
- Git commit history
- progress.txt log
- prd.json task state
- AGENTS.md semantic memory

### AGENTS.md (Passive Context)
- **Passive** = always in system prompt, no decision to search
- **100% pass rate** vs 79% for dynamic skills (Vercel tests)
- Contains: patterns, conventions, gotchas, recent learnings
- Superior to skills for framework-specific knowledge

### Architecture Evolution
- **Compound AI Systems** > monolithic models
- **Subagent-as-a-Tool**: Encapsulate capabilities in callable sub-agents
- **EDDOps**: Evaluation-Driven Development and Operations
- **NEXUS AI**: Ghost Mode for autonomous computer use

### Technical Innovations
- **Superposition Prompting**: 93x faster, 43% more accurate
- **Inference-Efficient Scaling**: Wider, shallower models
- **ReAct 3.0**: Systole/Diastole cycles (biological inspiration)

---

## 📚 Papers Referenced
- 2406.00584 - Compound AI Systems
- 2411.13768 - EDDOps
- 2404.06910 - Superposition Prompting
- 2501.18107 - Inference-Efficient Scaling
- 2412.00535 - FullStack Bench

## 🔗 Key Concepts
- Context Collapse
- Comprehension Debt
- AI-Legible Code
- Architecture Decision Records (ADR)
- 8000 token context limit rule

---

---

## 🔄 Ralph Wiggum Deep Dive

### Valore del "Contesto Stateless"
- **Affidabilità**: Evita accumulo di confusione/allucinazioni
- **Efficienza**: Previene context rot in sessioni prolungate

### 4 Canali di Memoria Persistente
1. **AGENTS.md** (Memoria Semantica) - convenzioni, gotchas, ri-iniettato ogni turno
2. **Git Commit History** - evoluzione fisica del codice
3. **progress.txt** - diario attività per debug/audit
4. **prd.json** - task state, "bussola" dello sciame

### Enterprise Integration
- Abilita shift imperativo → dichiarativo
- Umano definisce criteri di successo + test
- Loop opera autonomo (es. di notte)
- Ogni modifica: piccola, testata, documentata
- Riduce Comprehension Debt

---

## 🏭 Workflow Operativo Enterprise

### 6 Pilastri Fondamentali

1. **Ciclo Ralph Wiggum** - micro-task atomici con context reset
2. **EDDOps** - valutazione continua come funzione di governo permanente
3. **Streams & Sessions** - event-driven orchestration
4. **Swarm Multi-Agente**:
   - Planner + Board (votazione pesata)
   - Subagent-as-a-Tool
   - LLM-as-a-Judge (panel di modelli diversi)
5. **Test-First Methodology**:
   - Spec Phase → Test-First → Implement → Review Indipendente
6. **Human-in-the-Loop**:
   - Guardian Mode (rischio classificato)
   - Auditability (Temporal Replay)

### Sistema Dissipativo
Workflow = sistema che consuma risorse per mantenere ordine
- **Sistole** = attività esterna
- **Diastole** = consolidamento interno

---

## 🔗 AGENTS.md + Ralph Wiggum Integration

### Flow Operativo
```
1. INIZIO TASK
   └── Leggi AGENTS.md → inject in system prompt
   
2. IMPLEMENTAZIONE  
   └── Usa pattern/gotchas dal file
   
3. CHIUSURA TASK
   └── Aggiorna AGENTS.md con nuove scoperte
   └── Reset context
   └── Loop
```

### Perché Funziona
- **Passive Context** = sempre presente, no decisione "se cercare"
- **Evoluzione Continua** = ogni ciclo arricchisce la knowledge base
- **Passaggio testimone** = agente v1 → agente v2 tramite file

> "L'AGENTS.md trasforma il loop da azioni isolate a processo evolutivo"

---

## 🏗️ Ecosistema 2026: Framework DOE

### Transizione Radicale
- Sviluppatore = "architetto di intenti", non amanuense
- Valore professionale = precisione della direzione, non velocità scrittura

### DOE Framework
```
D - DIRECTIVE     → Obiettivi in linguaggio naturale (markdown)
O - ORCHESTRATION → AI pianifica connessioni (MCP, API)
E - EXECUTION     → AI scrive ed esegue codice
```

### Self-Annealing (Auto-ricottura)
Sistemi che leggono propri error messages e stack traces per auto-correggersi.

### Paradosso della Produttività
| Metrica | Trend |
|---------|-------|
| PR speed | +20% |
| Incidenti PR | +23.5% |

**Problema**: Volume > Capacità di review → "AI slop"
**Soluzione**: Verifica automatica (Code Rabbit, harness)

### Multi-Terminale Pattern
- Claude Code creator: 5-10 terminali paralleli
- Vibe Kanban + git worktrees
- Branch separati per evitare merge hell

### Competenze 2026

| ❌ Obsolete | ✅ Cruciali |
|-------------|-------------|
| Sintassi manuale | System Thinking (API, data flows) |
| Algoritmi avanzati | Plan Mode (PRD dettagliati) |
| Debug sintassi | Agent Orchestration (MCP) |

### Metafora Finale
> Sviluppo = cantiere automatizzato
> - Developer = capocantiere (planimetria)
> - Agents = robot (esecuzione)
> - Tests = sensori sicurezza

---

*Source: NotebookLM conversation dump*
