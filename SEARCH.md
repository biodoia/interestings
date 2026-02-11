# GoFainder - Motori di Ricerca 🔍

> Comandi per cercare nuovi tool e progetti

## 🌐 Ricerche Web

### GitHub Trending
```bash
# Go projects
gh api /search/repositories -q '.items[] | "\(.full_name) ⭐\(.stargazers_count) - \(.description)"' \
  --jq '.items[:20]' -f q='language:go stars:>100 pushed:>2025-01-01' -f sort=stars

# AI coding tools
gh api /search/repositories \
  -f q='ai coding agent cli stars:>500' -f sort=stars | jq '.items[:15] | .[] | {name, url: .html_url, stars: .stargazers_count, desc: .description}'

# MCP servers
gh api /search/repositories \
  -f q='mcp server model context protocol' -f sort=updated | jq '.items[:10]'
```

### Ricerche Specifiche

```bash
# Parallel agents
gh api /search/repositories -f q='parallel agents orchestration ai' -f sort=stars

# Vibe coding / spec-driven
gh api /search/repositories -f q='spec driven development ai' -f sort=stars

# Code review AI
gh api /search/repositories -f q='ai code review automated' -f sort=stars

# Tree-sitter parsing
gh api /search/repositories -f q='tree-sitter code analysis go' -f sort=stars

# RAG systems
gh api /search/repositories -f q='rag retrieval augmented generation code' -f sort=stars
```

---

## 🔎 Query Patterns

### Per Linguaggio
```bash
# Go
gh api /search/repositories -f q='language:go topic:ai topic:cli stars:>50' -f sort=updated

# Rust (spesso ha pattern interessanti)
gh api /search/repositories -f q='language:rust topic:ai topic:terminal' -f sort=stars

# TypeScript (MCP ecosystem)
gh api /search/repositories -f q='language:typescript mcp server' -f sort=stars
```

### Per Topic
```bash
# Agent orchestration
gh api /search/repositories -f q='topic:agent-orchestration OR topic:multi-agent' -f sort=stars

# Code generation
gh api /search/repositories -f q='topic:code-generation topic:ai' -f sort=stars

# Terminal UI
gh api /search/repositories -f q='topic:tui topic:ai OR topic:llm' -f sort=stars
```

---

## 🤖 Automazione Ricerca

### Script: Cerca e Salva

```bash
#!/bin/bash
# gofainder-search.sh

QUERY="$1"
OUTPUT="search-results-$(date +%Y%m%d).md"

echo "# Ricerca: $QUERY" > "$OUTPUT"
echo "Data: $(date)" >> "$OUTPUT"
echo "" >> "$OUTPUT"

gh api /search/repositories -f q="$QUERY" -f sort=stars | \
  jq -r '.items[:20] | .[] | "## \(.full_name)\n- ⭐ \(.stargazers_count)\n- 🔗 \(.html_url)\n- 📝 \(.description // "N/A")\n- 📦 \(.language // "N/A")\n"' >> "$OUTPUT"

echo "Salvato in $OUTPUT"
```

### Uso:
```bash
./gofainder-search.sh "ai coding agent cli"
./gofainder-search.sh "parallel agents orchestration"
./gofainder-search.sh "mcp server typescript"
```

---

## 📊 Categorie di Ricerca

### 1. Orchestrazione Multi-Agent
```
ai agent orchestration parallel
multi agent framework coding
swarm agents development
```

### 2. Code Analysis
```
tree-sitter code analysis
ast parsing semantic
code understanding llm
```

### 3. Memory & RAG
```
rag retrieval code
memory layer ai agent
vector database code
```

### 4. CI/CD & DevOps
```
ai devops automation
code review automated ai
ci cd ai agent
```

### 5. Spec-Driven Development
```
spec driven development
plan execute ai coding
requirements to code
```

### 6. MCP Ecosystem
```
mcp server model context
mcp tools integration
model context protocol
```

---

## 🗂️ Template Analisi

Quando trovi un progetto interessante, crea file in `analysis/`:

```markdown
# [Nome Progetto]

**URL:** https://github.com/...
**Stars:** X
**Language:** Go/Rust/TypeScript
**Last Update:** YYYY-MM-DD

## Descrizione
...

## Funzionalità Chiave
- Feature 1
- Feature 2

## Pattern Interessanti
- Pattern 1: descrizione
- Pattern 2: descrizione

## Relevanza per Autoschei
⭐⭐⭐⭐⭐ (1-5)

### Cosa integrare:
- [ ] Pattern X in ComponenteY
- [ ] Feature Z in ComponenteW

## Comandi/Uso
\`\`\`bash
...
\`\`\`
```

---

## 🔄 Workflow Consigliato

1. **Cerca** con query sopra
2. **Filtra** per stars > 100 e ultimo update < 3 mesi
3. **Analizza** README e codice
4. **Documenta** in `analysis/XX-nome.md`
5. **Registra** in `URLS.md`
6. **Valuta** integrazione in `autoschei/docs/EXTERNAL_INTEGRATIONS.md`

---

## 🌟 Fonti Alternative

### Awesome Lists
- https://github.com/awesome-selfhosted/awesome-selfhosted
- https://github.com/f/awesome-chatgpt-prompts
- https://github.com/steven2358/awesome-generative-ai
- https://github.com/e2b-dev/awesome-ai-agents

### Hacker News
```bash
# Cerca su HN (via API)
curl "https://hn.algolia.com/api/v1/search?query=ai+coding+agent&tags=story" | jq '.hits[:10]'
```

### Reddit
- r/LocalLLaMA
- r/ChatGPTCoding
- r/MachineLearning

### Twitter/X
- @kaborobot
- @simonw
- @swyx
