# Bottegaiarda: Autonomous Coding Bible & Swarm LLM Architecture
> From NotebookLM analysis 2026-02-10

---

## Overview

Bottegaiarda è un ecosistema integrato per lo sviluppo software autonomo che combina:
- **Autonomous Coding Bible (ACB)** - Regole e struttura agentica
- **Swarm LLM Architecture** - Infrastruttura massivamente parallela

**Obiettivo**: Risolvere il paradosso dell'IA nel coding - la rimozione della "frizione" decisionale che porta all'accumulo di debito tecnico invisibile.

---

## 1. Architettura a 14 Agenti e 4 Layer

### Layer 1: Orchestration
| Agente | Modello | Funzione |
|--------|---------|----------|
| Supreme Orchestrator | Premium | Coordina l'intero workflow |
| Task Router | Cheap | Smistamento task |
| Priority Manager | Cheap | Gestione priorità |

### Layer 2: Sentinel (Sistema Immunitario)
| Agente | Modello | Funzione |
|--------|---------|----------|
| Code Archaeologist | Free | Contesto storico file legacy |
| Pattern Architect | Cheap | Validazione conformità pattern |
| Debt Sentinel | Cheap | Blocca se debt score > 50 |
| Security Auditor | Cheap | Scansione vulnerabilità |

### Layer 3: Coding
| Agente | Modello | Funzione |
|--------|---------|----------|
| Feature Architect | Premium | Architettura feature |
| Implementation Coder | Premium | Scrittura codice |
| Test Engineer | Cheap | Generazione test |
| Refactor Oracle | Premium | Rifattorizzazione strutturale |

### Layer 4: Infrastructure
| Agente | Modello | Funzione |
|--------|---------|----------|
| Git Manager | Free | Operazioni Git |
| CI/CD Controller | Cheap | Pipeline automation |
| Deploy Agent | Cheap | Deploy management |
| Monitor Daemon | Free | Osservazione produzione |

---

## 2. I Dieci Comandamenti

1. **Non codificare mai al buio** - Richiede pacchetti di contesto
2. **Rifattorizza, non rattoppare** - Strutturale > patch
3. **Il Pattern Registry è il DNA sacro**
4. **Debt Score < 50 o merge bloccato**
5. **Complessità ciclotomatica < 15**
6. **Pattern compliance > 80%**
7. **Test coverage delta mai negativo**
8. **Security vulnerabilities = 0**
9. **Ogni commit deve superare 5 Quality Gates**
10. **Il Refactor Oracle interviene sempre sui blocchi**

---

## 3. Quality Gates

| Gate | Metrica | Soglia |
|------|---------|--------|
| 1 | Complessità ciclotomatica | < 15 per funzione |
| 2 | Indice manutenibilità | > 40 |
| 3 | Pattern compliance | > 80% |
| 4 | Test coverage delta | ≥ 0 |
| 5 | Security vulnerabilities | = 0 |

---

## 4. Infrastruttura Ibrida (4 Tier)

### Tier 1: Piani Forfettari (Paid)
- Claude Code, Google, OpenAI
- Zhipu GLM, Kimi K2, MiniMax
- Per task critici e ragionamento profondo
- Costo: fisso mensile

### Tier 2: API Free Legittime
- Groq, Google AI Studio, OpenRouter Free
- Per task ad alta frequenza, non critici
- Costo: zero (rate limited)

### Tier 3: GPU Locali
- RTX 4060 (8GB), RTX 4070 Super Ti (16GB)
- Target: aggiungere scheda 24GB
- Ollama/vLLM per inferenza
- Costo: zero variabile, massima privacy

### Tier 4: Emergenza (GPT4Free)
- Fork GPT4Free
- Solo quando altri tier falliscono
- Per task non critici/sperimentali

**Costo stimato workflow**: $0.10 - $0.15

---

## 5. Gateway Go-Based (Bifrost Wrapper)

### Perché Go invece di Python/LiteLLM?

| Metrica | LiteLLM | Bifrost |
|---------|---------|---------|
| Overhead latenza | 500µs | **11µs** |
| RAM | 372MB | **120MB** |
| Concorrenza | Python GIL | **Goroutine native** |

### Stack Tecnologico

```
┌─────────────────────────────────────────────────────┐
│                 REVERSE PROXY LAYER                  │
│        (httputil.ReverseProxy con Rewrite)          │
└─────────────────────────┬───────────────────────────┘
                          │
┌─────────────────────────┴───────────────────────────┐
│                      go-chi                          │
│              (Middleware chains)                     │
└─────────────────────────┬───────────────────────────┘
                          │
┌─────────────────────────┴───────────────────────────┐
│                     BIFROST                          │
│                 (Core gateway)                       │
└─────────────────────────────────────────────────────┘
```

### Componenti

| Componente | Tecnologia | Funzione |
|------------|------------|----------|
| HTTP Router | go-chi | Middleware chains |
| Reverse Proxy | httputil.ReverseProxy | Rewrite (Go 1.20+) |
| Database | pgx + sqlc | Type-safe SQL |
| Time Series | TimescaleDB | Metriche latenza |
| Rate Limiting | go-redis + redis_rate | GCRA algorithm |
| Caching | Redis | Semantic caching |
| Scraping | Colly + Rod | Discovery provider |
| Scheduling | robfig/cron | Health checks |
| Concurrency | errgroup.SetLimit | Parallel benchmarks |
| Hot Reload | Yaegi | Plugin routing |
| TUI | Charm Bubble Tea | Real-time monitoring |

---

## 6. Intelligent Routing (Capability-Based)

### Virtual Endpoints

| Nome Logico | Funzione |
|-------------|----------|
| `fast-go-coder` | Modelli veloci specializzati Go |
| `deep-reasoner` | Modelli ragionamento profondo |
| `long-context-analyst` | Modelli con contesto lungo |

### Strategie Load Balancing
- **Weighted Round-Robin** - Per capacità
- **Latency-based** - Tempi risposta recenti
- **Cost-based** - Ottimizzazione costi

### Circuit Breaker
- Cooldown 30 secondi dopo 3 fallimenti
- Evita sovraccarico provider instabili

### Capability Registry
Database che traccia:
- Reasoning depth score
- Coding quality (per linguaggio)
- Context window effettiva (testata con RULER)
- Ranking ELO dinamico

---

## 7. Discovery e Benchmarking Autonomo

### Discovery Agent
- Web scraping GitHub, Reddit, forum
- Usa Colly (pagine statiche) + Rod (JavaScript)
- Scopre nuovi endpoint gratuiti

### Mini-Benchmark Suites (~15 min)
- **HumanEval-mini** - Coding quality
- **RULER** - Context window reale
- **Custom reasoning** - Depth test

### Ranking ELO
- Performance aggregate nel tempo
- Affidabilità statistica
- Aggiornamento dinamico

---

## 8. Swarm Intelligence

### Micro-Tasking
- Task semplificati al massimo
- 100 task simultanei
- Modelli ultra-leggeri (<20B parametri)

### Statistiche (RouterBench)
> 52.8% dei prompt può essere gestito ottimamente da modelli sotto i 20B di parametri

### Execution Pattern
```
Orchestrator → divide in 100 micro-task
    → routing a modelli specializzati
    → esecuzione parallela
    → aggregazione risultati
    → validazione Sentinel
    → merge o retry
```

---

## 9. Sentinel Protocol (Dettaglio)

### Flusso di Validazione

```
Code prodotto
    │
    ▼
┌─────────────────────┐
│ Code Archaeologist  │ → Recupera contesto storico
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  Pattern Architect  │ → Verifica conformità pattern
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│   Debt Sentinel     │ → Calcola debt score
└──────────┬──────────┘
           │
    ┌──────┴──────┐
    │             │
Score ≤ 50    Score > 50
    │             │
    ▼             ▼
┌─────────┐  ┌─────────────┐
│ PROCEED │  │ Refactor    │
└─────────┘  │ Oracle      │
             └─────────────┘
                   │
                   ▼
             Rifattorizzazione
             strutturale
```

---

## 10. Mapping a Autoschei

| Bottegaiarda | Autoschei | Status |
|--------------|-----------|--------|
| Supreme Orchestrator | gommander | ⚠️ Parziale |
| Code Archaeologist | memogo | ⚠️ Parziale |
| Pattern Architect | goaiaiai | ⚠️ Parziale |
| Debt Sentinel | goaiaiai | ❌ Missing |
| Implementation Coder | gociccidai | ✅ Esiste |
| Git Manager | ghrego | ✅ Esiste |
| Deploy Agent | govai | ✅ Esiste |
| Bifrost Gateway | - | ❌ Missing |
| 4-Tier Routing | - | ❌ Missing |

### Gap Critici
1. **Bifrost wrapper** - Go gateway ad alte prestazioni
2. **Debt Sentinel** - Blocco automatico su debt score
3. **4-Tier Routing** - Gestione ibrida provider
4. **Discovery Agent** - Scoperta automatica API free
5. **Capability Registry** - Database competenze modelli

---

## Metafore Chiave

### Centrale Elettrica
> L'infrastruttura ibrida è come una centrale elettrica intelligente: generatori interni (GPU locali), contratto a canone fisso (piani forfettari), pannelli solari (API Free). Il gateway decide ogni microsecondo quale fonte usare.

### Ufficio Postale
> Lo stack Go è il sistema nervoso di un ufficio postale ultra-moderno: go-chi riceve i pacchi; sqlc/TimescaleDB sono gli archivi; go-redis è il cronometro; Yaegi è il manuale riscritto in tempo reale.

### Cattedrale Gotica
> L'architettura è una cattedrale automatizzata: agenti di Coding = operai; Sentinel = maestri d'ascia con laser; ACB = registro disegni immutabile; Swarm Gateway = logistica che consegna materiale perfetto.

---

*Extracted: 2026-02-10*
