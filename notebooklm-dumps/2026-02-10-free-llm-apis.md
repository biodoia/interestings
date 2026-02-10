# Free LLM API Resources - Comprehensive List

*Source: https://github.com/cheahjs/free-llm-api-resources*

## Quick Summary

| Provider | Best For | Limits |
|----------|----------|--------|
| OpenRouter | Best variety (30+ free models) | 20 req/min, 50 req/day |
| Groq | Fast inference | 14,400 req/day (Llama 3.1 8B) |
| Google AI Studio | Gemini models | 250K tokens/min |
| NVIDIA NIM | Enterprise models | 40 req/min |
| Cloudflare Workers | Edge inference | 10K neurons/day |
| Cerebras | Large models | 30 req/min |
| HuggingFace | Any open model | $0.10/month credits |

---

## Free Providers

### OpenRouter
**URL**: https://openrouter.ai

**Limits**: 20 requests/minute, 50 requests/day (1000 req/day with $10 topup)

**Free Models**:
- `google/gemma-3-12b-it:free`
- `google/gemma-3-27b-it:free`
- `google/gemma-3-4b-it:free`
- `meta-llama/llama-3.1-405b-instruct:free`
- `meta-llama/llama-3.2-3b-instruct:free`
- `meta-llama/llama-3.3-70b-instruct:free`
- `mistralai/mistral-small-3.1-24b-instruct:free`
- `qwen/qwen3-4b:free`
- `qwen/qwen3-coder:free`
- `openai/gpt-oss-120b:free`
- `openai/gpt-oss-20b:free`
- `tngtech/deepseek-r1t-chimera:free`
- `tngtech/deepseek-r1t2-chimera:free`
- `z-ai/glm-4.5-air:free`
- `nvidia/nemotron-nano-12b-v2-vl:free`
- `moonshotai/kimi-k2:free`
- And 15+ more...

### Google AI Studio
**URL**: https://aistudio.google.com

**Warning**: Data used for training outside UK/CH/EEA/EU

**Limits**:
- Gemini 3 Flash: 250K tokens/min, 20 req/day
- Gemini 2.5 Flash: 250K tokens/min, 20 req/day
- Gemma 3 series: 15K tokens/min, 14.4K req/day

### NVIDIA NIM
**URL**: https://build.nvidia.com/explore/discover

**Requirements**: Phone number verification

**Limits**: 40 requests/minute

### Mistral (La Plateforme)
**URL**: https://console.mistral.ai/

**Requirements**: Phone verification, opt-in to data training

**Limits**: 1 req/sec, 500K tokens/min, 1B tokens/month

### Mistral (Codestral)
**URL**: https://codestral.mistral.ai/

**Limits**: 30 req/min, 2K req/day

### HuggingFace Inference Providers
**URL**: https://huggingface.co/docs/inference-providers/en/index

**Limits**: $0.10/month in credits

### Vercel AI Gateway
**URL**: https://vercel.com/docs/ai-gateway

**Limits**: $5/month

### Cerebras
**URL**: https://cloud.cerebras.ai/

**Limits**:
- Llama 3.3 70B: 30 req/min, 64K tokens/min
- gpt-oss-120b: 30 req/min, 60K tokens/min
- Qwen 3 32B: 30 req/min, 64K tokens/min

### Groq
**URL**: https://console.groq.com

**Best limits**:
- Llama 3.1 8B: 14,400 req/day, 6K tokens/min
- Llama 3.3 70B: 1K req/day, 12K tokens/min
- Allam 2 7B: 7K req/day, 6K tokens/min
- Whisper: 7,200 audio-sec/min

### Cohere
**URL**: https://cohere.com

**Limits**: 20 req/min, 1K req/month

### GitHub Models
**URL**: https://github.com/marketplace/models

**Limits**: Based on Copilot subscription tier

### Cloudflare Workers AI
**URL**: https://developers.cloudflare.workers-ai

**Limits**: 10,000 neurons/day

**Models**:
- Llama 3.3 70B Instruct
- Llama 3.2 11B Vision
- Mistral Small 3.1 24B
- Gemma models
- Qwen models
- DeepSeek variants

---

## Providers with Trial Credits

| Provider | Credits | Best For |
|----------|---------|----------|
| Fireworks | $1 | Quick testing |
| Baseten | $30 | Production trial |
| Nebius | $1 | European providers |
| Novita | $0.5/1year | Long-term testing |
| AI21 | $10/3mo | Jamba models |
| Upstage | $10/3mo | Solar models |
| NLP Cloud | $15 | Various models |
| Modal | $5/mo | Compute flexibility |

---

## For Autoschei Integration

**Priority additions**:
1. **Groq** - Best ratio of limits/quality for Llama models
2. **Cloudflare Workers AI** - Free edge inference
3. **Cerebras** - Large model access
4. **NVIDIA NIM** - Enterprise-grade
5. **Mistral Codestral** - Coding specialization

**Consider replacing**:
- bifrost-free → maximhq/bifrost (complete gateway)
