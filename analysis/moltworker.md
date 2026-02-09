# Moltworker - OpenClaw su Cloudflare Workers

> Fonte: https://blog.cloudflare.com/moltworker-self-hosted-ai-agent/

## Overview

**Moltworker** (8.2k ⭐) permette di eseguire OpenClaw (ex Moltbot/Clawdbot) su Cloudflare Workers invece che su hardware locale (Mac mini).

## Architettura

```
┌─────────────────────────────────────────────────────────────┐
│                    Cloudflare Edge                          │
│  ┌─────────────────────────────────────────────────────┐   │
│  │              Moltworker (Entry Worker)               │   │
│  │   - API Router                                       │   │
│  │   - Admin UI                                         │   │
│  │   - Proxy to Sandbox                                 │   │
│  └─────────────────────────────────────────────────────┘   │
│                           │                                 │
│  ┌──────────┬─────────────┼─────────────┬──────────────┐   │
│  │          │             │             │              │   │
│  ▼          ▼             ▼             ▼              ▼   │
│ ┌────┐  ┌───────┐  ┌───────────┐  ┌─────────┐  ┌──────┐   │
│ │ R2 │  │Browser│  │  Sandbox  │  │   AI    │  │Access│   │
│ │    │  │Render │  │ Container │  │ Gateway │  │ Auth │   │
│ └────┘  └───────┘  └───────────┘  └─────────┘  └──────┘   │
└─────────────────────────────────────────────────────────────┘
```

## Componenti Cloudflare Utilizzati

### 1. Sandbox SDK
- **Cosa:** Container isolati per eseguire codice untrusted
- **API:** `@cloudflare/sandbox`
- **Features:**
  - `sandbox.exec()` — esegui comandi
  - `sandbox.mkdir()` — gestione file
  - `sandbox.createCodeContext()` — interprete Python/JS
  - `sandbox.mountBucket()` — monta R2 come filesystem
- **Costo:** ~$34.50/mo (container 24/7) o ~$10/mo (4h/day con sleep)

```typescript
import { getSandbox } from '@cloudflare/sandbox';

const sandbox = getSandbox(env.Sandbox, 'user-123');
const result = await sandbox.exec('python --version');
```

### 2. AI Gateway
- **Cosa:** Proxy centralizzato per tutti i provider AI
- **Features:**
  - BYOK (Bring Your Own Key) — gestione chiavi centralizzata
  - **Unified Billing** — paga Cloudflare, loro pagano i provider
  - Fallback automatico tra provider
  - Analytics e logging
  - Rate limiting e spend limits
  - Zero Data Retention (ZDR) per OpenAI/Anthropic
- **Uso:** Basta settare `ANTHROPIC_BASE_URL` al gateway endpoint

```bash
# Unified Billing - niente API key, solo crediti CF
curl -X POST https://gateway.ai.cloudflare.com/v1/{account_id}/{gateway_id}/compat/chat/completions \
  --header 'cf-aig-authorization: Bearer {CLOUDFLARE_TOKEN}' \
  --data '{"model": "google-ai-studio/gemini-2.5-pro", ...}'
```

### 3. Browser Rendering
- **Cosa:** Chromium headless programmabile
- **Supporta:** Playwright, Puppeteer, Stagehand, MCP
- **Uso in Moltworker:**
  - CDP proxy da Sandbox a Browser Rendering
  - Skill iniettata nel runtime

### 4. R2 Storage
- **Cosa:** Object storage S3-compatibile
- **Uso:** Persistence per session, memory, conversations
- **Mount:** `sandbox.mountBucket()` lo monta come filesystem locale

### 5. Zero Trust Access
- **Cosa:** Autenticazione/autorizzazione
- **Protegge:** Admin UI, API endpoints
- **Metodi:** Email OTP, Google, GitHub, etc.

## Costi Stimati

| Componente | Costo |
|------------|-------|
| Workers Paid plan | $5/mo |
| Container (24/7) | ~$29.50/mo |
| Container (4h/day) | ~$5-6/mo |
| R2, Browser, Access | Free tier sufficiente |
| **Totale (always-on)** | **~$34.50/mo** |
| **Totale (on-demand)** | **~$10-15/mo** |

## Setup Rapido

```bash
# Clone
git clone https://github.com/cloudflare/moltworker
cd moltworker
npm install

# Configura API key (o usa Unified Billing)
npx wrangler secret put ANTHROPIC_API_KEY

# Genera gateway token
export MOLTBOT_GATEWAY_TOKEN=$(openssl rand -hex 32)
npx wrangler secret put MOLTBOT_GATEWAY_TOKEN

# Deploy
npm run deploy

# Accedi
open https://your-worker.workers.dev/?token=$MOLTBOT_GATEWAY_TOKEN
```

## Vantaggi vs Mac Mini

| Aspetto | Mac Mini | Moltworker |
|---------|----------|------------|
| Costo iniziale | ~$700+ | $0 |
| Costo mensile | Elettricità | ~$10-35 |
| Manutenzione | Manuale | Zero |
| Scaling | Limitato | Automatico |
| Uptime | Dipende | 99.99% |
| Browser | Locale | Edge globale |
| Storage | Locale | R2 distribuito |

## Integrazioni Rilevanti per GoBro

### 1. Sandbox SDK → Per esecuzione codice
```go
// GoBro potrebbe usare Sandbox per:
// - Eseguire tool calls in isolamento
// - Processare file in sicurezza
// - Eseguire script generati da LLM
```

### 2. AI Gateway → Per multi-provider
- Unified Billing elimina gestione chiavi
- Fallback automatico (come nostro fallback.go!)
- Analytics centralizzate

### 3. Browser Rendering → Per web browsing
- Già supporta MCP
- Playwright nativo

## Link Utili

- **Repo:** https://github.com/cloudflare/moltworker
- **Sandbox SDK:** https://developers.cloudflare.com/sandbox/
- **AI Gateway:** https://developers.cloudflare.com/ai-gateway/
- **Browser Rendering:** https://developers.cloudflare.com/browser-rendering/
- **Unified Billing:** https://developers.cloudflare.com/ai-gateway/features/unified-billing/

## Note per Autoschei

1. **Considerare Cloudflare Workers** come deployment alternativo a VPS
2. **AI Gateway Unified Billing** semplificherebbe gestione provider
3. **Sandbox SDK** potrebbe sostituire container locali per tool execution
4. **Pattern architetturale** simile a nostro GoBro → Providers → Tools
