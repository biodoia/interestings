# OpenHands Deep Dive - 2026 Analysis

*Source: Grok response to Sergio's query - 2026-02-11*

---

## Cos'è OpenHands?

**OpenHands** (ex-OpenDevin) - Piattaforma open-source per agenti di coding cloud-based.

| Metric | Value |
|--------|-------|
| **Stars** | 67.7K |
| **Forks** | 8.4K |
| **Contributors** | 469 |
| **Company** | All Hands AI |
| **Lead** | Graham Neubig |

### Filosofia

> "AI-Driven Development toolkit" - delega task da GitHub, GitLab, Slack

**Confronto**:
- **vs Devin** (closed): Più accessibile, gratis, vendor-agnostic
- **vs Aider** (CLI): Più enterprise, ecosystem completo
- **vs SWE-agent** (academic): Più production-ready

### Claims
- 87% issue fixing same-day (real-world)
- Bate Devin su accessibilità, ma non su autonomy pura (70%+)

---

## Architettura SDK

### Core Components

```
┌─────────────────────────────────────────────────────────┐
│              OpenHands Software Agent SDK                 │
├─────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐   │
│  │ Core Engine │  │   Tools &   │  │Sandboxing  │   │
│  │ (loop)      │  │  Subagents  │  │ (Docker)    │   │
│  └─────────────┘  └─────────────┘  └─────────────┘   │
├─────────────────────────────────────────────────────────┤
│              Event Stream                               │
│         (risolve "identity amnesia")                     │
├─────────────────────────────────────────────────────────┤
│  Integrazioni: GitHub Actions, CI/CD, Slack           │
└─────────────────────────────────────────────────────────┘
```

### Key Features

1. **Core Engine**
   - Loop: Osserva → Pianifica → Agisci
   - Supporto multi-agent (swarm scaling a migliaia)

2. **Tools & Subagents**
   - Browser/desktop control
   - File CRUD
   - Shell exec
   - Git integration
   - Delegation pattern (analysis agent, fixing agent)

3. **Sandboxing**
   - Docker-based per sicurezza enterprise
   - Evita che AI rompa il repo

4. **Event Stream**
   - Risolve "identity amnesia" (agenti che dimenticano chi sono)
   - Boost performance 20-30% su benchmark

### LLM Support

- Claude, GPT, Qwen
- Custom models
- **OpenHands LM** (32B beast)

---

## Benchmark e Performance

### SWE-Bench Results

| Configuration | Verified | Lite |
|---------------|----------|------|
| **CodeAct 2.1 + Claude 3.5** | **53%** | 41.7% |
| **CodeAct 2.1 + Qwen3-235B** | 34.4% | - |
| **OpenHands LM (32B)** | 37.4% | - |
| **Baseline (Event Stream)** | 32.7% | - |

### Real-World Performance

- **87%** issue fixing same-day (production claim)
- **~80%** su "real edits" (practical)
- **20-30%** boost da Event Stream

### Opinion

> "Benchmark sono overrated per enterprise – OpenHands brilla in real-world"

Consigliato: Testa sui tuoi repo legacy prima di fidarti.

---

## Usage Examples

### CLI Quickstart

```bash
openhands --model claude-3.5-sonnet --task "Fix bug in main.py"
```

Output: Genera → Testa → Committa

### Autonomous Loop (GitHub Action)

```yaml
# Tag issue con "fix me", agente parte
- name: OpenHands Fix
  uses: openhands/github-action@v1
  with:
    task: "Fix issue ${{ github.event.issue.number }}"
```

Per continuous iteration: Wrap in **Ralph Loop-style reset**

### Multi-Agent (SDK)

```python
from openhands import Agent

# Swarm pattern
agent = Agent(
    model='gpt-4o',
    tools=['git', 'shell', 'browser']
)

agent.run(task="Implement feature X", repo="my-repo")
```

### Enterprise

- Cloud deployment con observability
- Eval-driven ops con logs + metrics
- Self-hosted con Ollama + Qwen3 (team Hyderabad example)

---

## Community e Adoption

### Stats
- **Contributors**: 180+
- **Slack**: Thriving community

### Real-World Usage
- **CMU**: Research
- **Team Hyderabad**: Self-hosted security (Ollama + Qwen3)

### Limitazioni
- GPU-heavy per local (12GB+ VRAM)
- Agents possono "amnesiare" senza tuning

---

## Opinion e Raccomandazioni

### Pro
- **Ecosistema completo**: SDK + CLI + GUI + Cloud
- **Production-ready**: Sandboxing, security, scalability
- **Open-source**: Non vendor-locked

### Contro
- **Dipende da LLM sottostante**: Se usi modello scarso = incidenti
- **GPU requirements**: Heavy per local deployment
- **Tuning necessario**: Per evitare amnesia

### Raccomandazione di Grok

> "Provalo su un side-project, integra con FrameGoTUI per dashboard stiloso"

Se non convince: "Sarò sincero, forse è hype al 70%"

---

## Confronto con Nostro Stack

| Feature | OpenHands | GOLEM/Autoschei |
|---------|-----------|-----------------|
| **LLM** | Claude/GPT/Qwen (any) | Z.AI + OpenRouter |
| **Memory** | Event Stream | memogo (System 1+2) |
| **Tools** | Built-in SDK | ghrego, govai, gommander |
| **Sandboxing** | Docker | Systemd (less secure) |
| **CLI** | openhands CLI | GOLEM CLI |
| **GUI** | Web-based | FrameGoTUI |
| **Multi-agent** | Native (1000+) | Design phase |
| **Benchmark** | 53% SWE-Bench Verified | TBD |

### Cosa Possiamo Imparare

1. **Event Stream** → Implementare in GOLEM
2. **Sandboxing** → Migliorare con Docker containers
3. **CLI UX** → openhands CLI come reference
4. **SDK pattern** → Tools come composable units

---

## Prossimi Passi (se interessa)

1. **Testare OpenHands** su un side-project
2. **Integrare con FrameGoTUI** (dashboard per agent monitoring)
3. **Studiare Event Stream** per GOLEM
4. **Benchmark comparison** con nostri tool

---

*Document Source: Grok response - 2026-02-11*
