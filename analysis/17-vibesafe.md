# VibeSafe

**URL:** https://github.com/slowcoder360/vibesafe

## Overview
AI-native DevSecOps CLI. Security scanner per vibe coding.

## Stack
- Node.js (npm install -g vibesafe)
- OSV.dev per CVE database
- OpenAI per fix suggestions (optional)
- MIT License

## Concept
Catch vulnerabilities, secrets, insecure configs, hallucinated dependencies BEFORE ship.

## Scans
1. **Secrets** — AWS keys, JWTs, SSH keys, high-entropy, .env
2. **Dependency CVEs** — check vs OSV.dev (direct deps)
3. **Insecure configs** — DEBUG=true, devMode, permissive CORS
4. **HTTP clients** — missing timeouts/abort controllers (axios, fetch, got)
5. **Upload validation** — missing size/type checks (multer, formidable)
6. **Exposed endpoints** — /admin, /debug, /metrics (incl Next.js API)
7. **Missing rate limiting** — heuristic check
8. **Unsafe logging** — sensitive info leaks, full error stacks

## Killer Feature: vibesafe install
```bash
vibesafe install express
```
Anti-typosquatting/slopsquatting checks:
- Package age (flags if < 30 days)
- Download volume (flags if low)
- README presence
- License check
- Repository/homepage check

User confirmation before install if warnings found.

## Commands
```bash
vibesafe scan                    # scan current dir
vibesafe scan --high-only        # critical only
vibesafe scan -r report.md       # markdown report
vibesafe scan --url http://localhost:11434 --model gemma3  # local LLM
vibesafe install pkg -- --save-dev  # secure install
```

## Pattern Interessanti
1. **Security-first vibe coding** — catch AI-generated vulns
2. **Safe install wrapper** — npm install con checks
3. **Local LLM support** — non solo OpenAI
4. **Heuristic scanning** — pattern detection
5. **.vibesafeignore** — custom exclusions

## Pro
- Comprehensive security scans
- Anti-slopsquatting
- AI fix suggestions
- Local LLM option
- Easy integration

## Contro
- Node.js only (package.json deps)
- Heuristic-based (false positives)
- Lockfile support coming soon

## Idee Riutilizzabili
- Secure package install wrapper
- Anti-typosquatting heuristics
- Security scan as pre-commit/CI step
- AI-generated fix suggestions
- Local LLM fallback option
