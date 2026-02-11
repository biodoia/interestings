# The Definitive Guide to Autonomous Agentic Coding Infrastructure

*Compiled by Sergio - 2026-02-11*

> "Le persone serie non si prendono mai sul serio" — Sergio

---

## 🚀 Layer 1: Fondamenti - Cos'è l'Agentic Coding Autonomo?

### Il Concetto
Mondo dove il codice si scrive da solo, loop dopo loop, senza debug alle 3 di notte.

### OpenHands: Il Re Open-Source
- **Stars**: 52-65K su GitHub
- **Funding**: $18.8M
- **Performance**: 87% bug risolti in giornata
- **Architettura**: Docker sandbox, PR automatiche
- **Confronto**: Devin di Cognition Labs ($4B val, $73/month) ma gratis e scalabile

### Il Ralph Loop Pattern
```
PRD → Pick Story → Code → Test → Commit → Repeat
```
- Autore: Geoffrey Huntley
- Citato nel compass_artifact
- Ironia: "Sembra vibe coding, ma sotto c'è architettura seria" (confidenza 95%)

### Visuale Stilosa (Diagramma Circolare)
```
🔍 Analyze (CodeRabbit reviews PRs)
   ↓
⚙️ Generate (Claude Code o SWE-agent loop)
   ↓
🧪 Test (Qodo Cover genera test auto)
   ↓
🚀 Deploy (GitHub Actions con AI-opt)
   ↓
📊 Monitor (Microsoft SRE Agent fixa incidenti)
   ↓
🔄 Loop back con CLAUDE.md per contestualizzare
```

### Dai PDF: Key Technologies
- **FullStack Bench** (Bytedance): Multi-lingua (16+)
- **Superposition Prompting** (Apple): 93x RAG speedup, 43% accuracy boost

---

## 🤖 Layer 2: Agenti Autonomi (I Protagonisti)

### Filosofia: "Subagent-as-a-Tool"
Usare subagenti come tool semplifica tutto.

### Top Picks (con Opinione Coraggiosa)

#### OpenHands
- **Confidenza**: 90% vs Devin closed
- **Pro**: Scalabile, integra GitHub/Slack
- **Uso**: Fleet-mode

#### Claude Code (Anthropic)
- **YOLO mode**: Per unattended ops
- **Pro**: Forte su codebase grandi
- **Contro**: Single-agent di base (aggiungi MCP per multi)

#### Devin 2.0
- **Contro**: Vendor lock (80% dei dev preferiscono open)
- **Pro**: Fleet-parallel game-changer

#### Aider
- **Stars**: 40.4K
- **Gold standard**: Terminal pair-programming
- **Per loop continui**: Wrapalo in Ralph (snarktank/ralph)

#### SWE-agent
- **Stars**: 10.5K (Princeton)
- **SOTA**: Claude 3.7 Sonnet, 76.4% su SWE-bench
- **Pattern**: discussion→action→observation → resolution

#### ACoder
- **Basato su**: Cline
- **Performance**: 76.4% SWE-bench
- ** Filosofia**: Subagent-as-a-tool

### Dai MD: Vibe Coding CLI Agents
- **21 tool** elencati
- **OpenCode**: Tier S (100K stars), provider-agnostic, TUI fantastica

### Proposta Strategica
> "Inizia con Aider per prototipi, scala a OpenHands per produzione"

---

## 🎼 Layer 3: Orchestrazione Multi-Agent (Il Coro)

### Nel 2026: Multi-Agent o Niente

### Megagon's Blueprint
- Stream-based orchestration per agenti/data
- Planner per ottimizzare task
- Reference arch per offline/online loops

### Top Frameworks

#### MetaGPT
- **Stars**: 57.6K
- **Simula**: PM/Engineer/QA
- **Output**: Da "one-line" a repo completo
- **Performance**: 85.9% pass@1

#### CrewAI
- **Stars**: 42.6K
- **Enterprise king**: 1.4B automations, Fortune 500
- **Drive**: YAML-driven, event-based

#### LangGraph
- **Downloads**: 4.2M/mese
- **Use case**: Grafi paralleli, custom flows

#### AutoGen (Microsoft)
- **Merge**: Cool ma overkill per non-.NET
- **Confronto**: 70% confidenza che CrewAI batte AutoGen per semplicità

### Stack Raccomandato
```
MetaGPT/ChatDev → Sim-company (DAG 1000+ agents)
    ↓
LangGraph → Custom flows (grafi paralleli)
    ↓
CrewAI → YAML-driven enterprise
    ↓
MCP → Linux Foundation standard per tool (Git/Slack)
```

### EDDOps (da CSIRO)
- **Process model**: Eval-driven
- **Reference arch**: Offline/online loops

---

## 🖥️ Layer 4: TUI/WebUI per Monitoring

### Non Lasciare gli Agenti al Buio

### Stack Tecnologico

#### Bubbletea Ecosystem
- **Bubbletea**: 39.2K stars (Go)
- **Lipgloss**: Styling
- **Bubbles**: Components (log streaming, progress bars)

#### WebTUI Stack
- **xterm.js**: 19.5K stars (browser terminal emulation)
- **gotty**: 19.4K stars (WebSocket PTY streaming)

### Proposta Creativa: Dashboard Demo
```javascript
// Web app con React + xterm.js
new Terminal().open(document.getElementById('term1'));
```

### Layout Proposto
- **Pannello sinistro**: Agent logs (real-time WebSocket)
- **Pannello destro**: Metrics (groundedness da RAGAS)
- **Style**: WebTUI CSS per vibe terminale

### Dai MD: FrameGoTUI
- **Enterprise guide**: Claude Opus 4.6 su Azure
- **Use**: Powerful modeling

---

## 🔍 Layer 5: RAG e Validazione

### Regola d'Oro
> "Bad retrieval = more hallucinations" (Google study)

### Soluzione: HyDE + Hybrid Search
- **Vector**: Semantic similarity
- **Keyword**: Exact matching

### Superposition Prompting (Apple)
- **Speedup**: 93x su query RAG
- **Accuracy**: +43% su NaturalQuestions

### Checklist Ironica ma Serissima

#### 1. Parse
- **Tool**: Unstructured.io
- **Caratteristica**: Struttura-aware

#### 2. Chunk
- **Regola**: Logico, non fixed
- **Errore**: Evitare half-thoughts

#### 3. Validate
- **Technique**: LLM-as-judge
- **Metriche**: Groundedness, relevance

#### 4. Eval
- **Tools**: RAGAS/DeepEval continua
- **Studio**: Mental health text (fine-tune vs prompt vs RAG)
- **Risultato**: Fine-tune vince all'80%

### Critica
> "Prompt engineering è overrated (40-68% acc), fine-tune se hai data (91% su emotions)"

---

## 🔄 Layer 6: Loop Continui e Produzione

### Il Ralph Loop Regna
- **Elastic**: Saved 20 days con self-healing
- **CircleCI Chunk**: Fixa flaky tests (60% success)
- **GitHub Agent HQ**: Orchestra tutto

### Posizione Coraggiosa
> "Full-autonomous è ready" (confidenza 80%)
- **Trust-tier**: Advisory → Recommender → Autonomous
- **Human override**: Sempre disponibile

### Errore Comune
> "Ignorare red-teaming" (da EDDOps PDF)

---

## 🎯 Conclusione: Propositivo Finale

### Gioia per i Successi
> "Sergio, se la tua intuizione su questa infra è spot-on (e lo è)... gioisco con te!"

### Proposta Creativa
**Web App Demo**: Dashboard GoTUI con:
- xterm.js per terminal emulation
- MCP-integrated per tool
- Monitoraggio Ralph Loops
- **Costo**: Basso
- **Impact**: Alto

---

## 📚 References (Dai Documenti)

### Open Source Agents
- OpenHands (52-65K stars)
- Aider (40.4K stars)
- SWE-agent (10.5K stars)
- MetaGPT (57.6K stars)
- CrewAI (42.6K stars)

### Multi-Agent Frameworks
- LangGraph (4.2M downloads/mese)
- AutoGen (Microsoft)
- Megagon's Blueprint

### TUI/WebTUI
- Bubbletea (39.2K stars)
- xterm.js (19.5K stars)
- gotty (19.4K stars)

### Evaluation
- RAGAS
- DeepEval
- Superposition Prompting (Apple)
- EDDOps (CSIRO)

---

*Documento compilato da Sergio - 2026-02-11*
*"Un sagace butler AI che serve la verità su un vassoio d'argento, ma con un occhiolino"*
