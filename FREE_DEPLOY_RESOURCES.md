# 🆓 Risorse Gratuite per Deploy AI/Agents

> Mappatura per non dipendere dalla macchina locale

## 🚀 Hosting/Compute

### Tier S (Best Free)

| Servizio | Free Tier | Ideale per |
|----------|-----------|------------|
| **Fly.io** | 3 shared VMs, 160GB transfer | Go servers, WebSocket |
| **Railway** | $5/mo credit, 500h | Quick deploys, preview |
| **Render** | 750h/mo, spin down | APIs, cron jobs |
| **Cloudflare Workers** | 100k req/day | Edge functions, AI Gateway |
| **Vercel** | 100GB bandwidth, serverless | Frontend, API routes |
| **Deno Deploy** | 100k req/day | TypeScript edge |

### Tier A (Good Free)

| Servizio | Free Tier | Note |
|----------|-----------|------|
| **Hugging Face Spaces** | CPU gratuita | ML models, Gradio apps |
| **Replit** | Always-on con limits | Dev/test |
| **Glitch** | 1000h/mo | Node.js apps |
| **Cyclic** | 100k req/mo | Serverless Node |

## 🧠 AI/LLM APIs

### Gratis o Generosi

| Provider | Free Tier | Modelli |
|----------|-----------|---------|
| **Groq** | 30 req/min | Llama 3.3, Mixtral, Whisper |
| **Google AI Studio** | 60 req/min | Gemini 2.5 Pro/Flash |
| **Anthropic** | $5 credit | Claude 3.5 |
| **OpenRouter** | Free models | Llama, Mistral, etc |
| **Together AI** | $25 credit | OSS models |
| **Mistral** | Limited free | Mistral Large |
| **Cerebras** | Fast inference | Llama 3.3 70B |
| **SambaNova** | Free tier | Fast Llama |

### STT/TTS Gratis

| Provider | Free Tier |
|----------|-----------|
| **Groq Whisper** | 30 req/min |
| **Deepgram** | $200 credit |
| **AssemblyAI** | 3h/mo |
| **ElevenLabs** | 10k chars/mo |
| **Play.ht** | 12.5k chars |

## 🗄️ Database/Storage

| Servizio | Free Tier |
|----------|-----------|
| **Supabase** | 500MB, 2GB transfer |
| **PlanetScale** | 5GB, 1B reads |
| **Turso** | 9GB, 500M reads |
| **Neon** | 3GB Postgres |
| **Upstash** | 10k cmd/day Redis |
| **Cloudflare R2** | 10GB storage |
| **Backblaze B2** | 10GB storage |

## 🔧 Per GoBro Specifico

### Architettura Consigliata (100% Free)

```
┌─────────────────────────────────────────────────┐
│                   Cloudflare                     │
│  ┌─────────────┐  ┌─────────────┐               │
│  │ AI Gateway  │  │   Workers   │               │
│  │ (unified)   │  │ (edge API)  │               │
│  └─────────────┘  └─────────────┘               │
└─────────────────────────────────────────────────┘
            │                │
            ▼                ▼
┌─────────────────┐  ┌─────────────────┐
│    Fly.io       │  │   Upstash       │
│  (Go server)    │  │ (Redis queue)   │
│  3 VMs free     │  │ 10k/day free    │
└─────────────────┘  └─────────────────┘
            │
            ▼
┌─────────────────────────────────────────────────┐
│              AI Providers (rotate)               │
│  Groq → Google → OpenRouter → Cerebras          │
└─────────────────────────────────────────────────┘
```

### Deploy Commands

```bash
# Fly.io (Go)
fly launch --no-deploy
fly deploy

# Cloudflare Workers
wrangler deploy

# Railway
railway up

# Render
# Push to GitHub, auto-deploy
```

## 📱 Mobile Backend

| Per Android | Opzione |
|-------------|---------|
| **Firebase** | Spark free (auth, DB, hosting) |
| **Supabase** | Auth + Realtime free |
| **Appwrite** | Self-host o cloud free |

## 🎯 Quick Start per GoBro

1. **Server**: Fly.io (Go binary, WebSocket support)
2. **AI**: Cloudflare AI Gateway (unified billing, fallback)
3. **STT**: Groq Whisper (velocissimo, free)
4. **LLM**: Rotate: Groq → Google → OpenRouter
5. **TTS**: ElevenLabs (10k chars) o edge TTS
6. **DB**: Turso (SQLite at edge)
7. **Queue**: Upstash Redis

## 💰 Stima Costi Reali

Con free tiers ottimizzati:
- **Light usage** (dev/test): $0/mo
- **Medium** (100 users): $5-15/mo
- **Heavy** (1000+ users): $30-50/mo

---

*Ultimo update: 2026-02-09*
