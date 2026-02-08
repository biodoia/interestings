# VibEx-CLI

**URL:** https://github.com/Gymnott1/VibeEx-CLI

## Overview
Context preparation tool per AI coding assistants. Combina, pulisce, protegge codice.

## Stack
- Node.js (npm install -g vibex-cli)
- MIT License

## Concept
Non è un coding agent — prepara codice da passare agli AI assistants.

## Problema Risolto
- Context window pieno di commenti/noise
- Secrets esposti accidentalmente (API keys, tokens)
- File sparsi difficili da condividere

## Feature Chiave
1. **Combine files** → singolo `vx_{project}.txt`
2. **Remove comments** (`--rc`) → reduce tokens
3. **Scrub secrets** (`--rp`) → sostituisce patterns sensibili
4. **Monitor mode** (`-mx`) → auto-update on change
5. **Trim ranges** (`--trim`) → include solo parti specifiche
6. **Cut ranges** (`--cut`) → exclude parti specifiche
7. **Exclude patterns** (`-x`) → skip folders/files

## Privacy Patterns Detected
- API keys → "API_KEY"
- Auth tokens → "AUTH_TOKEN"
- Email addresses
- Phone numbers
- Personal tokens
- Secret codes

## Commands
```bash
vx c                        # combine all
vx c -f src/ -x tests/      # include/exclude
vx c --rc --rp              # remove comments + secrets
vx c -mx                    # monitor mode
vx c --trim="s-200"         # first 200 chars only
vx c --cut="300-500"        # exclude range
```

## Pattern Interessanti
1. **Preprocessing layer** — tra codebase e AI
2. **Secret scrubbing** — pattern replacement
3. **Character range operations** — precision context control
4. **Monitor mode** — live reload del context file
5. **Single output file** — easy paste to AI

## Pro
- Protegge secrets automaticamente
- Reduce token usage (no comments)
- Simple workflow
- Monitor mode per iterazione

## Contro
- Non è un agent (solo preprocessing)
- Manual paste to AI
- No semantic understanding

## Idee Riutilizzabili
- Preprocessing layer per context preparation
- Secret pattern detection/replacement
- Character range trim/cut
- Monitor mode per auto-update
- Single combined output file pattern
