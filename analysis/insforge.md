# InsForge

## Overview
Backend development platform built for AI coding agents and AI code editors.

## Key Features
- **Semantic Layer**: Between AI agents and backend primitives
- **MCP Integration**: Full MCP server support
- **Backend Primitives**:
  - Authentication (user management, sessions)
  - Database (Postgres)
  - Storage (S3 compatible)
  - Edge Functions (serverless)
  - Model Gateway (OpenAI compatible, multi-provider)
  - Site Deployment

## Architecture
```
AI Coding Agents
      ↓
InsForge Semantic Layer
      ↓
┌─────────────────────────────────────┐
│ Auth │ DB │ Storage │ Functions │ AI │
└─────────────────────────────────────┘
```

## Deployment Options
- Cloud: insforge.dev
- Self-hosted: Docker Compose
- One-click: Railway, Zeabur, Sealos

## Relevance for Autoschei
- **HIGH**: Semantic layer concept = what GoBro needs
- Backend primitives exposed via MCP
- Could be used as reference for govai deployment module

## Links
- https://github.com/InsForge/InsForge
- https://insforge.dev
- https://docs.insforge.dev
