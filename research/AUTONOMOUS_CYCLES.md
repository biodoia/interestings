# Cicli Autonomi su GitHub - Research Report

*Scandagliato il 2026-02-10*

## 🏆 TOP TIER (>1000 ⭐)

### 1. cline/cline - 57,739 ⭐
**URL**: https://github.com/cline/cline
**Pattern**: IDE-based autonomous agent
- Autonomous coding agent in VSCode
- Creates/edits files, executes commands, uses browser
- Permission-based execution
- Multi-step task completion

### 2. snarktank/ralph - 9,859 ⭐
**URL**: https://github.com/snarktank/ralph
**Pattern**: PRD-driven autonomous loop

**Core Concept:**
```
PRD → User Stories → Execute One Story → Commit → Repeat
```

**Key Files:**
- `ralph.sh` - Bash loop che spawna fresh AI instances
- `prd.json` - User stories con `passes: true/false`
- `progress.txt` - Append-only learnings
- `AGENTS.md` - Learnings per future iterazioni

**Critical Concepts:**
1. **Each Iteration = Fresh Context** - Nuovo AI ogni volta
2. **Memory via Git** - Storia persiste in git history
3. **Small Tasks** - Ogni story deve completarsi in un context window
4. **AGENTS.md Updates** - Post-iteration learnings
5. **Feedback Loops** - Typecheck, tests, CI must stay green

**Workflow:**
1. Create PRD with AI
2. Convert to `prd.json`
3. Run `ralph.sh [max_iterations]`
4. Loop until all stories `passes: true`

### 3. kodu-ai/claude-coder - 5,290 ⭐
**URL**: https://github.com/kodu-ai/claude-coder
**Pattern**: VSCode extension autonomous agent
- Step-by-step project building
- Latest automated coding technologies

---

## 🧬 SELF-IMPROVING SYSTEMS

### 4. lemoz/darwin-godel-machine - 10 ⭐ (ma MOLTO sofisticato)
**URL**: https://github.com/lemoz/darwin-godel-machine
**Pattern**: Evolutionary self-modification

**Core Concept:**
```
Agent → Self-Modify → Benchmark → Archive if Better → Repeat
```

**Architecture:**
- **DGM Controller** - Main evolution loop
- **Agent System** - LLM-powered coding agents
- **Archive Management** - Stores all valid agents with scores
- **Evaluation System** - Benchmark runner, validator, scorer
- **Self-Modification** - Diagnosis → Proposal → Implementation

**Memory Bank System:**
```
memory-bank/
├── productContext.md     # High-level project overview
├── activeContext.md      # Current status, priorities
├── systemPatterns.md     # Recurring patterns, decisions
├── decisionLog.md        # Significant decisions with rationale
└── progress.md           # Task tracking, completion
```

**Evolution Loop:**
1. Initialize with base agent
2. Select Parent (performance + novelty)
3. Self-Modify (analyze performance, propose improvements)
4. Implement (modify own code)
5. Evaluate (benchmark)
6. Archive if valid
7. Repeat

### 5. mmtmn/Darwin-Godel-Machine - 21 ⭐
**URL**: https://github.com/mmtmn/Darwin-Godel-Machine
**Pattern**: Local self-evolving AI

**Key Features:**
- Runs completely offline (Ollama + Llama 3)
- Archive of evolving agents
- Open-ended exploration
- Modular components

**Archive Output:**
```
archive/
├── initial_agent/
│   ├── code/
│   └── performance.txt
├── child_1f43b2c3_perf_0.450/
└── child_a92fbbc2_perf_0.681/
```

### 6. aviadr1/claude-meta - 7 ⭐
**URL**: https://github.com/aviadr1/claude-meta
**Pattern**: Meta-rules for continuous learning

**The Magic Prompt:**
```
"Reflect on this mistake. Abstract and generalize the learning. Write it to CLAUDE.md."
```

**Meta-Rules Structure:**
```markdown
## META - MAINTAINING THIS DOCUMENT

### Writing Effective Guidelines
1. Use absolute directives - Start with "NEVER" or "ALWAYS"
2. Lead with why - Explain the problem before the solution
3. Be concrete - Include actual commands/code
4. Minimize examples - One clear point per code block
5. Bullets over paragraphs

### Anti-Bloat Rules:
- ❌ Don't add "Warning Signs" to obvious rules
- ❌ Don't show bad examples for trivial mistakes
```

**Key Insight**: AI reads meta-rules → learns how to write rules → self-regulates quality

---

## 🔧 OTHER NOTABLE PROJECTS

### 7. OpenAlpha_Evolve - 968 ⭐
**URL**: https://github.com/shyamsaktawat/OpenAlpha_Evolve
**Pattern**: DeepMind AlphaEvolve inspired
- Autonomous evolution of code
- Benchmark-driven improvement

### 8. coleam00/Linear-Coding-Agent-Harness - 188 ⭐
**URL**: https://github.com/coleam00/Linear-Coding-Agent-Harness
**Pattern**: Linear integration
- Takes issues from Linear
- Autonomous implementation
- PR creation

### 9. TiMEM-AI/TiMEM-Evolve - 4 ⭐
**URL**: https://github.com/TiMEM-AI/TiMEM-Evolve
**Pattern**: Experience Learning System
- Continuous evolution
- Measurable improvement

---

## 🎯 PATTERN SYNTHESIS: Come costruire un ciclo autonomo

### Pattern A: PRD Loop (Ralph-style)
```bash
while [ stories_remaining ]; do
    pick_next_story
    spawn_fresh_ai_instance
    implement_story
    run_quality_checks
    if checks_pass; then
        commit
        mark_story_complete
        update_progress_file
    fi
done
```

**Files necessari:**
- `prd.json` - Task list con status
- `progress.txt` - Append-only context
- `AGENTS.md` - Learnings
- `loop.sh` - Main driver

### Pattern B: Evolutionary Loop (DGM-style)
```python
while True:
    parent = select_parent_from_archive()
    child = parent.self_modify()
    score = benchmark(child)
    if is_valid(child) and score > threshold:
        archive.add(child)
    if child.is_novel():
        explore_further(child)
```

**Files necessari:**
- `archive/` - Versioni agenti
- `memory-bank/` - Context persistente
- `benchmarks/` - Suite di test
- `evolution.py` - Main driver

### Pattern C: Meta-Learning Loop (claude-meta-style)
```
On Error:
  1. Reflect on mistake
  2. Abstract the pattern
  3. Generalize the learning
  4. Write to CLAUDE.md following meta-rules
  5. Future sessions read and apply
```

**Files necessari:**
- `CLAUDE.md` - Con sezione META
- Meta-rules per auto-regolazione

---

## 🔑 KEY INSIGHTS

1. **Fresh Context Every Iteration** - Non accumulare, resettare
2. **Memory via Files** - Git, progress.txt, AGENTS.md
3. **Small Atomic Tasks** - Una story per context window
4. **Feedback Loops Essential** - Tests, typecheck, benchmarks
5. **Archive Everything** - Ogni versione che funziona
6. **Meta-Rules** - Insegna all'AI come scrivere regole
7. **Novelty + Performance** - Non solo miglioramento, anche esplorazione

---

## 📚 RESOURCES

- Geoffrey Huntley's Ralph: https://ghuntley.com/ralph/
- Darwin Gödel Machine paper: https://arxiv.org/abs/2505.22954
- Sakana AI blog: https://sakana.ai/dgm/

---

## 🎯 APPLICAZIONE A AUTOSCHEI

Autoschei già implementa molti di questi pattern:

| Pattern | Autoschei Component | Status |
|---------|---------------------|--------|
| PRD Loop | progotti → gociccidai | ✅ |
| Quality Check | goaiaiai | ✅ |
| Memory | memogo (Cipher) | ✅ |
| Archive | ghrego (git) | ✅ |
| Deploy | govai | ✅ |
| Self-Modify | goaiaiai validates goaiaiai | 🔨 |

**Missing pieces per full autonomy:**
1. `ralph.sh` equivalent - Loop driver
2. `prd.json` format - Progotti output
3. Fresh context spawning - Sub-agent pattern
4. Benchmark suite - Per self-improvement
5. Archive of working versions

---

*Total repos analyzed: 50+*
*Top patterns identified: 3 (PRD Loop, Evolutionary, Meta-Learning)*
*Highest stars: cline (57K), ralph (9.8K), claude-coder (5.3K)*
