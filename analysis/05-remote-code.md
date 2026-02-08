# Remote Code - Claude Code in Your Pocket

**URL:** https://remote-code.com/  
**Tipo:** Prodotto commerciale (iOS app)  
**Stato:** TestFlight (Beta)

---

## Overview

Remote Code è un'app iOS che permette di usare **Claude Code dal telefono**, connettendosi al tuo computer. Il concept: continuare le sessioni di "vibe coding" quando lasci la scrivania.

Core idea: **AI coding companion che ti segue dal caffè al divano**.

---

## Stack Tecnologico (Dedotto)

| Component | Tecnologia |
|-----------|------------|
| **Mobile App** | iOS nativo (TestFlight) |
| **Desktop Agent** | "Remote Code Uplink" (installer) |
| **Comunicazione** | Pairing sicuro (phone ↔ computer) |
| **AI Backend** | Claude Code (via relay) |

---

## Architettura (Ipotizzata)

```
┌─────────────────────────────────────────────────────────┐
│                    📱 iPhone App                         │
│              Remote Code (TestFlight)                    │
│                                                          │
│   • Native mobile interface                              │
│   • Optimized for sending messages                       │
│   • Git integration UI                                   │
└───────────────────────┬─────────────────────────────────┘
                        │ Secure pairing
                        │
                        ▼
┌─────────────────────────────────────────────────────────┐
│              💻 Desktop (Uplink Agent)                   │
│                                                          │
│   ┌──────────────────────────────────────────────────┐  │
│   │            Remote Code Uplink                     │  │
│   │   • Pairing daemon                                │  │
│   │   • Message relay                                 │  │
│   │   • Session persistence                           │  │
│   └──────────────────────┬───────────────────────────┘  │
│                          │                               │
│   ┌──────────────────────▼───────────────────────────┐  │
│   │              Claude Code CLI                      │  │
│   │   • Actual AI coding work                         │  │
│   │   • File access                                   │  │
│   │   • Git operations                                │  │
│   └──────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## Feature Chiave

### 1. Mobile-First Interface
- UI nativa iOS ottimizzata per mobile
- Non un remote desktop laggy
- Non un terminale SSH raw

### 2. Secure Pairing
- Pairing one-time tra iPhone e computer
- "Pair your iPhone in seconds"

### 3. Git Integration
- Built-in git integration
- Rich interface (non solo command line)

### 4. Session Continuity
- "Never let your vibe coding session end"
- Sessioni persistenti tra mobile e desktop

---

## Confronto (dal sito)

| Aspetto | Remote Desktop Apps | SSH Terminal Apps | Remote Code |
|---------|---------------------|-------------------|-------------|
| Latency | Laggy | OK | Native |
| UI | Tiny, desktop-sized | Command-line only | Mobile-optimized |
| Git | Through remote desktop | Manual | Built-in |
| Flow | Breaks it | Breaks it | Maintains it |

---

## Pattern Interessanti

### 1. **Relay Architecture**
Mobile app non esegue Claude Code direttamente → relay tramite desktop agent.
Vantaggi:
- Usa auth/API keys del desktop
- Accesso filesystem locale
- Zero setup credentials su mobile

### 2. **Mobile-Optimized for Messaging**
UI pensata per **inviare messaggi** all'AI, non per coding tradizionale.
Shift paradigm: mobile = command center, desktop = execution.

### 3. **Pairing Model**
Come AirDrop/Handoff Apple: pairing iniziale, poi "just works".

### 4. **Uplink Agent**
Daemon desktop che funge da bridge → pattern riutilizzabile per qualsiasi mobile-to-desktop relay.

---

## Pro/Contro

### ✅ Pro
- **True mobile AI coding**: non workaround ma soluzione nativa
- **Maintains flow**: continua dove hai lasciato
- **Native UX**: non remote desktop laggy
- **Git built-in**: feature che manca ad alternative
- **Zero mobile setup**: tutto relay via desktop

### ❌ Contro
- **iOS only**: no Android (per ora?)
- **Closed source**: non ispezionabile
- **Beta (TestFlight)**: non production-ready
- **Dipendenza desktop**: computer deve essere online
- **Pricing unknown**: modello di business non chiaro
- **Limited info**: sito minimale, pochi dettagli tecnici

---

## Idee Riutilizzabili

1. **Desktop Relay Agent Pattern**
   - Mobile app si connette a agent desktop
   - Agent esegue comandi/relay con accesso locale
   - Utile per qualsiasi tool che richiede accesso filesystem

2. **Pairing UX**
   - One-time secure pairing
   - Poi connessione automatica
   - Come Bluetooth pairing ma per app-to-desktop

3. **Mobile as Command Center**
   - UI ottimizzata per inviare comandi, non per output dettagliato
   - Results principali su mobile, dettagli su desktop

4. **Uplink Daemon Pattern**
   - Background service sul desktop
   - WebSocket/similar per comunicazione real-time
   - Riutilizzabile per OpenClaw mobile?

5. **Vibe Coding Concept**
   - Marketing angle: "continue your flow anywhere"
   - UX focus su non-interruzione del flusso

---

## Applicabilità a OpenClaw

**Potenziale pattern interessante:** Mobile companion per OpenClaw

```
┌─────────────────────┐     ┌─────────────────────┐
│   OpenClaw Mobile   │◄───►│   OpenClaw Desktop  │
│   (iOS/Android)     │     │   (existing)        │
│                     │     │                     │
│   • Quick commands  │     │   • Full execution  │
│   • Notifications   │     │   • File access     │
│   • Status view     │     │   • Terminal        │
└─────────────────────┘     └─────────────────────┘
```

---

## Note Personali

Remote Code risolve un problema reale: vuoi continuare a interagire con il tuo AI coding assistant quando ti sposti. L'approccio relay via desktop agent è smart perché evita tutti i problemi di auth/credentials su mobile.

Il fatto che sia closed source e in beta limita l'ispezione tecnica, ma il concept è valido e il pattern relay è riutilizzabile.

**Interessante per**: pattern mobile-to-desktop relay, UX per mobile AI interaction, concept di "vibe coding continuity".

---

## Links

- **Site**: https://remote-code.com/
- **Install**: https://remote-code.com/install
- **TestFlight**: Disponibile (link su sito)
