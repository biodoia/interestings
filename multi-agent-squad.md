# Multi-Agent Squad - Production Multi-Agent Orchestration for Claude Code

**Repository:** https://github.com/bijutharakan/multi-agent-squad
**Type:** Framework / Orchestration System
**Status:** Open source

## What is Multi-Agent Squad?

An intelligent orchestration system that transforms Claude Code into a **complete software development team** with specialized AI agents, automated Git workflows, and enterprise-grade integrations.

Key insight: Instead of one monolithic AI, use **specialized agents** for different roles (PM, Architect, Backend, Frontend, QA, DevOps) coordinated by an orchestrator.

## Architecture

```
┌──────────────────────────────────────────────────────┐
│                 MULTI-AGENT SQUAD                     │
│                                                       │
│  ┌────────────────────┐  ┌─────────────────────┐     │
│  │     AI AGENTS      │  │   INTEGRATIONS      │     │
│  │                    │  │                     │     │
│  │  • Orchestrator    │  │  • Slack/Teams      │     │
│  │  • Product Mgr     │  │  • Jira/Linear      │     │
│  │  • Architect       │  │  • GitHub/GitLab    │     │
│  │  • Engineers       │  │  • CI/CD Tools      │     │
│  │  • QA/DevOps       │  │  • Monitoring       │     │
│  └────────────────────┘  └─────────────────────┘     │
│                                                       │
│  ┌────────────────────┐  ┌─────────────────────┐     │
│  │    MCP SERVERS     │  │    AUTOMATION       │     │
│  │                    │  │                     │     │
│  │  • Database        │  │  • Claude Hooks     │     │
│  │  • GitHub API      │  │  • Git Hooks        │     │
│  │  • Memory          │  │  • Sprint Mgmt      │     │
│  │  • Analytics       │  │  • PR Reviews       │     │
│  │  • Docker/K8s      │  │  • Quality Gates    │     │
│  └────────────────────┘  └─────────────────────┘     │
└──────────────────────────────────────────────────────┘
```

## Specialized Agent Roles

### Full-Stack Projects
| Agent | Responsibility |
|-------|----------------|
| 🎯 Prime Orchestrator | Manages entire workflow |
| 📊 Product Manager | Requirements, user stories |
| 🏗️ Solution Architect | System design |
| 💻 Backend Engineer | API development |
| 🎨 Frontend Engineer | User interface |
| ✅ QA Engineer | Testing |
| 🔧 DevOps Engineer | Deployment |

### API Projects
- API Architect, Backend Engineer, API Doc Specialist, Test Engineer

### Documentation Projects
- Technical Writer, Information Architect, Documentation Reviewer

## Key Features

### Enterprise Agile Workflow
- **Sprint Management** - Automated ceremonies and tracking
- **PR Review Cycles** - Enforced code review with comment resolution
- **Quality Gates** - Automated checks before phase transitions
- **Human Checkpoints** - Critical decisions require approval
- **Daily Standups** - Automated reminders and reports

### Natural Language Control
```
"I need to add user authentication"
"Help me set up CI/CD"
"Create API documentation"
"Review our architecture"
```

### Intelligent Automation (Claude Code Hooks)
Tell Claude what you want automated:
- "I forget to run tests" → Auto-runs tests after file changes
- "Remind me of daily standups" → 9 AM Slack/email reminders
- "Check code quality" → Auto-lint and format on save
- "Security checks" → Scan for secrets before commits

### 30+ Tool Integrations

**Project Management:**
- GitHub, Jira, Linear, Azure DevOps, ClickUp, Monday.com, Asana

**Communication:**
- Slack, Microsoft Teams, Discord, Email

**Development & DevOps:**
- GitHub Actions, Jenkins, GitLab CI, CircleCI
- Sentry, Datadog, Prometheus, New Relic
- BrowserStack, SonarQube, Cypress
- Confluence, Notion, GitHub Wiki

### MCP Server Support (14+ pre-configured)

**Data & Storage:**
- PostgreSQL Explorer - Natural language DB queries
- Memory Server - Persistent context across sessions
- Enhanced Filesystem - Advanced file ops

**Development Tools:**
- GitHub Integration - Deep PR/issue management
- Test Runner - Execute and monitor tests
- Docker Management - Container control
- Kubernetes - Deployment and pod management

**Communication:**
- Slack, Linear, Notion, Confluence servers

## Quick Start

```bash
# Clone
git clone https://github.com/bijutharakan/multi-agent-squad.git
cd multi-agent-squad

# Start Claude
claude

# Trigger orchestration
/project
```

## Project Structure (Flexible)

### Multi-Repo Web App
```
your-project/
├── CLAUDE.md           # Orchestration instructions
├── PROJECT.md          # Project details
├── projects/           # Your repos
│   ├── frontend/
│   └── backend/
├── docs/
└── .claude/agents/     # Your AI team
```

### Monorepo
```
your-project/
├── CLAUDE.md
├── PROJECT.md
├── src/
│   ├── frontend/
│   ├── backend/
│   └── shared/
├── docs/
└── .claude/agents/
```

## Smart Development Workflow

```
Requirements → PM agent creates specs
     ↓
Design → Architect creates system design
     ↓
Implementation → Engineers build it
     ↓
Testing → QA ensures quality
     ↓
Deployment → DevOps handles release
```

## Git Worktree Support

For parallel development across repos:
```bash
./scripts/worktree-manager.sh create-feature auth frontend backend
```

## Key Patterns

1. **Specialized Agents** - Different agents for different roles (not one monolithic AI)
2. **Orchestrator Pattern** - Central coordinator managing agent handoffs
3. **Human Checkpoints** - Critical decisions require human approval
4. **Quality Gates** - Automated checks between phases
5. **Memory Persistence** - MCP Memory Server for cross-session context
6. **Hook-based Automation** - Event-driven workflows
7. **Natural Language Control** - No complex CLI, just talk

Applicable to framegotui or any multi-agent orchestration system.

## Comparison with Other Approaches

| Feature | Multi-Agent Squad | Single Agent | Traditional Tools |
|---------|-------------------|--------------|-------------------|
| Specialization | ✅ Role-based | ❌ Generalist | ❌ N/A |
| Context | ✅ Shared via MCP | ❌ Session only | ❌ Manual |
| Orchestration | ✅ Automated | ❌ Manual | ❌ Manual |
| Quality Gates | ✅ Built-in | ❌ None | ⚠️ Separate tools |
| Integrations | ✅ 30+ tools | ❌ Limited | ⚠️ Per-tool |

---

*Added: 2026-02-08*
*Source: Sergio via WhatsApp*
