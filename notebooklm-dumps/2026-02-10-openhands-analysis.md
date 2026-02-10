# OpenHands SDK Analysis - Insights for Autoschei

## Overview

OpenHands è un SDK Python per agenti software con focus su:
- Skill system (AgentSkills standard + estensioni)
- Remote Agent Server (container-based)
- WebSocket streaming
- Workspace isolation

## Key Insights

### 1. Skill Loading Architecture (3 Types)

```python
repo_skills, knowledge_skills, agent_skills = load_skills_from_dir(skills_dir)
```

| Type | Description | When Loaded |
|------|-------------|-------------|
| `repo_skills` | AGENTS.md style | Always (conversation start) |
| `knowledge_skills` | knowledge/ subdirs | Progressive disclosure |
| `agent_skills` | SKILL.md files | Triggered or on-demand |

**Difference from our approach**: We have `autoschei-skill` following the same pattern. OpenHands confirms the pattern is valid.

### 2. Keyword Triggers (OpenHands Extension)

```python
from openhands.sdk.context import Skill, KeywordTrigger

Skill(
    name="encryption-helper",
    content="Use encrypt.sh for encryption",
    trigger=KeywordTrigger(keywords=["encrypt", "decrypt"]),
)
```

When user says "encrypt this", content is injected:
```
<EXTRA_INFO>
Skill location: /path/to/encryption-helper
Use the encrypt.sh script to encrypt messages.
</EXTRA_INFO>
```

**Idea**: Add keyword triggers to our autoschei-skill for specific modules (e.g., "deploy" → govai context).

### 3. Remote Agent Server Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Client (Python SDK)                      │
│         Conversation → RemoteConversation                    │
├─────────────────────────────────────────────────────────────┤
│                    Agent Server                             │
│         HTTP/WebSocket + Agent + Workspace                  │
├─────────────────────────────────────────────────────────────┤
│                    Workspace                                │
│         Docker container / Remote VM / Local                │
└─────────────────────────────────────────────────────────────┘
```

**Key classes**:
- `DockerWorkspace` - Isolated containers
- `APIRemoteWorkspace` - Remote via API (runtime.all-hands.dev)
- `LocalWorkspace` - Same process

**For GOLEM**: We could implement a similar architecture in Go:
- GOLEMWorkspace interface
- DockerRemoteWorkspace
- LocalWorkspace
- All implementing same API

### 4. Event Streaming

```python
def on_event(event):
    print(f"Received: {type(event).__name__}")

conversation = Conversation(
    agent=agent,
    workspace=workspace,
    callbacks=[on_event],
)
```

Real-time streaming of agent events via WebSocket. This is what makes remote agents feel "local".

### 5. Public Skills Repository

```python
from openhands.sdk.context.skills import load_public_skills

public_skills = load_public_skills()  # Clones from GitHub
```

OpenHands maintains `github.com/OpenHands/skills` with community skills. We could do similar with:
- `github.com/biodoia/autoschei-skills` (public registry)
- Git-based caching in `~/.config/autoschei/skills/`

### 6. Workspace Operations (Language-Agnostic)

```python
workspace.file_upload(local_path, remote_path)
workspace.file_download(remote_path, local_path)
result = workspace.execute_command("ls -la")
```

The workspace abstracts file/command operations regardless of execution environment. This is the key to "switching is just changing the workspace argument".

## Comparison with Our Stack

| Feature | OpenHands | Our Stack (Autoschei/GOLEM) |
|---------|-----------|----------------------------|
| Language | Python | Go |
| Skills | SKILL.md + triggers | SKILL.md (no triggers yet) |
| Remote Server | Docker/API | Not yet implemented |
| Event Streaming | WebSocket | Not yet implemented |
| Workspace Abstraction | Yes | goaiaiai partial |
| Multi-Agent | Agent delegation | 14-agent swarm |

## Potential Integrations

1. **Keyword Triggers** - Add to autoschei-skill for context injection
2. **Remote Agent Pattern** - Implement in GOLEM for containerized agents
3. **Public Skills Registry** - Create biodoia/autoschei-skills
4. **Event Streaming** - Add WebSocket support to goaiaiai

## Code References

- Agent Server: `https://github.com/OpenHands/software-agent-sdk`
- Remote Conversation: `openhands-sdk/openhands/sdk/conversation/impl/remote_conversation.py`
- Workspace Base: `openhands-sdk/openhands/sdk/workspace/base.py`
