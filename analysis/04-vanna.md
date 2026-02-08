# Vanna 2.0 - Text-to-SQL via LLM Agents

**URL:** https://github.com/vanna-ai/vanna  
**Licenza:** MIT  
**Stato:** Attivo (v2.0 major rewrite)

---

## Overview

Vanna trasforma **domande in linguaggio naturale in query SQL** usando LLM con Agentic Retrieval. La versione 2.0 è un complete rewrite focalizzato su:

- **User-aware**: ogni componente conosce l'identità utente
- **Enterprise security**: row-level security, audit logs
- **Web-first**: componente `<vanna-chat>` pronto all'uso

Core concept: **Natural language → SQL → Answers, con permessi user-aware**.

---

## Stack Tecnologico

| Component | Tecnologia |
|-----------|------------|
| **Backend** | Python (FastAPI/Flask) |
| **Frontend** | Web Component (`<vanna-chat>`) |
| **LLM Support** | OpenAI, Anthropic, Ollama, Azure, Gemini, Bedrock, Mistral |
| **Database Support** | PostgreSQL, MySQL, Snowflake, BigQuery, Redshift, SQLite, Oracle, SQL Server, DuckDB, ClickHouse |
| **Streaming** | Server-Sent Events (SSE) |
| **Visualization** | Plotly |

---

## Architettura

```
┌─────────────────────────────────────────────────────────┐
│                    👤 User                               │
│         "Show Q4 sales for my region"                   │
└───────────────────────┬─────────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────────┐
│               🌐 <vanna-chat>                            │
│         Web Component (React/Vue/HTML)                   │
└───────────────────────┬─────────────────────────────────┘
                        │ POST /api/vanna/v2/chat_sse
                        │ (with auth cookies/JWT)
                        ▼
┌─────────────────────────────────────────────────────────┐
│               🐍 Your Server (FastAPI)                   │
│                                                          │
│  ┌─────────────────────────────────────────────────┐    │
│  │              UserResolver                        │    │
│  │   Extract user from cookies/JWT/session         │    │
│  │   → User(id, email, group_memberships)          │    │
│  └──────────────────────┬──────────────────────────┘    │
│                         │                                │
│  ┌──────────────────────▼──────────────────────────┐    │
│  │                   Agent                          │    │
│  │   • LLM Service (Anthropic, OpenAI, etc.)       │    │
│  │   • Tool Registry                                │    │
│  │   • User Context                                 │    │
│  └──────────────────────┬──────────────────────────┘    │
│                         │                                │
│  ┌──────────────────────▼──────────────────────────┐    │
│  │                   Tools                          │    │
│  │   RunSqlTool (with row-level security)          │    │
│  │   Custom tools (EmailTool, etc.)                │    │
│  └──────────────────────┬──────────────────────────┘    │
└─────────────────────────┼───────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────┐
│                    📊 Database                           │
│         (with row-level security applied)                │
└─────────────────────────────────────────────────────────┘
                          │
                          │ Streaming response
                          ▼
┌─────────────────────────────────────────────────────────┐
│              📱 Streaming Components                     │
│   Progress → SQL Block → Table → Chart → Summary        │
└─────────────────────────────────────────────────────────┘
```

---

## Feature Chiave

### 1. User-Aware at Every Layer
```python
class MyUserResolver(UserResolver):
    async def resolve_user(self, request_context: RequestContext) -> User:
        token = request_context.get_header('Authorization')
        user_data = self.decode_jwt(token)
        
        return User(
            id=user_data['id'],
            email=user_data['email'],
            group_memberships=user_data['groups']  # Per permissions
        )
```
L'identità fluisce attraverso: system prompts → tool execution → SQL filtering.

### 2. Web Component Pronto all'Uso
```html
<script src="https://img.vanna.ai/vanna-components.js"></script>
<vanna-chat
  sse-endpoint="https://your-api.com/chat"
  theme="dark">
</vanna-chat>
```
- Usa cookies/JWT esistenti
- Works con React, Vue, o plain HTML

### 3. Streaming Response
Output in real-time:
1. Streaming Progress Updates
2. SQL Code Block (solo per admin)
3. Interactive Data Table
4. Charts (Plotly)
5. Natural Language Summary

### 4. Row-Level Security
Query automaticamente filtrate per permessi utente:
```python
# User con group_memberships=['read_sales']
# La query viene modificata per filtrare solo i dati accessibili
```

### 5. Custom Tools Pattern
```python
class EmailTool(Tool[EmailArgs]):
    @property
    def access_groups(self) -> list[str]:
        return ["send_email"]  # Permission check
    
    async def execute(self, context: ToolContext, args: EmailArgs) -> ToolResult:
        user = context.user  # Automatically injected
        # Business logic...
```

### 6. Enterprise Features
- **Lifecycle Hooks**: quota checking, logging, content filtering
- **LLM Middlewares**: caching, prompt engineering, cost tracking
- **Conversation Storage**: persist history per user
- **Observability**: tracing e metrics built-in

---

## Pattern Interessanti

### 1. **User-Aware Tool Execution**
`ToolContext` include sempre `user` → ogni tool può applicare permessi.

### 2. **access_groups Pattern**
Ogni tool dichiara quali gruppi possono usarlo:
```python
@property
def access_groups(self) -> list[str]:
    return ["admin", "data_analyst"]
```

### 3. **Streaming Structured UI**
Non streaming di testo, ma di **componenti UI strutturati**:
- `Table(data)`
- `Chart(plotly_json)`
- `Progress(message)`

### 4. **UserResolver Pattern**
Abstraction per estrarre user da qualsiasi auth system (JWT, cookies, OAuth).

### 5. **Tool Registry**
```python
tools = ToolRegistry()
tools.register(RunSqlTool(...))
tools.register(EmailTool())
```
Pattern plugin per tools custom.

### 6. **Legacy Adapter**
`LegacyVannaAdapter` per wrappare v0.x e ottenere nuova UI → migration path elegante.

---

## Pro/Contro

### ✅ Pro
- **Enterprise-ready**: security, audit, permissions out of the box
- **Web component**: UI pronta, zero frontend work
- **Multi-LLM**: qualsiasi provider supportato
- **Multi-DB**: praticamente ogni database SQL
- **User-aware**: identity flow attraverso tutto lo stack
- **Streaming**: UX moderna con feedback real-time
- **Extensible**: custom tools, hooks, middlewares

### ❌ Contro
- **Complessità**: molti concetti da capire per setup custom
- **Python-only**: backend deve essere Python
- **v2.0 breaking changes**: migration da v0.x richiede refactoring
- **Dipendenza LLM**: qualità SQL dipende dal modello
- **Costi**: chiamate LLM per ogni query

---

## Idee Riutilizzabili

1. **UserResolver Abstraction**
   - Pattern per estrarre user identity da qualsiasi auth
   - Riutilizzabile in qualsiasi sistema multi-tenant

2. **Tool with access_groups**
   - Ogni tool dichiara chi può usarlo
   - Enforcement automatico

3. **Streaming Structured Components**
   - SSE con payload strutturati (`type: 'table'`, `type: 'chart'`)
   - Frontend renderizza in base al type

4. **ToolContext Injection**
   - User, request, session auto-iniettati nel context
   - Tool non deve preoccuparsi di ottenerli

5. **Lifecycle Hooks Pattern**
   - `on_request`, `on_tool_call`, `on_response`
   - Per logging, rate limiting, content filtering

6. **Tool Registry Pattern**
   - Registration centralizzata di tools
   - Discovery automatico disponibilità

---

## Caso d'Uso: Production Setup

```python
from vanna import Agent
from vanna.servers.fastapi.routes import register_chat_routes
from vanna.integrations.anthropic import AnthropicLlmService
from vanna.tools import RunSqlTool
from vanna.integrations.sqlite import SqliteRunner

# 1. User resolver (your auth)
class MyUserResolver(UserResolver):
    async def resolve_user(self, request_context):
        token = request_context.get_header('Authorization')
        return User(id=..., email=..., group_memberships=[...])

# 2. Agent setup
agent = Agent(
    llm_service=AnthropicLlmService(model="claude-sonnet-4-5"),
    tool_registry=tools,
    user_resolver=MyUserResolver()
)

# 3. Register routes
register_chat_routes(app, ChatHandler(agent))
```

---

## Note Personali

Vanna 2.0 è un esempio eccellente di come fare enterprise-grade text-to-SQL. Il pattern user-aware attraverso tutto lo stack è particolarmente elegante. Il web component pronto all'uso abbassa drasticamente la barrier to entry.

**Interessante per**: chi vuole aggiungere natural language query a database esistenti, pattern di user-aware tooling, streaming structured responses.
