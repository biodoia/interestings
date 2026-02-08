# Entelligence CLI

**URL:** https://entelligence.ai/cli

## Overview
Code review CLI per sviluppo AI-driven. Review locale prima del commit.

## Stack
- CLI tool
- Freemium (rate limited free tier)

## Feature Chiave
- Review pre-commit (non post-PR)
- Feedback diretto in terminal
- Context-aware (capisce dipendenze)
- Catch "AI slop" — hallucinations, logic errors, missed tests
- Pass feedback to AI coding agent

## Pattern Interessanti
1. **Local review loop** — code → review → fix → commit (tutto in terminal)
2. **AI backstop** — layer di validazione per codice AI-generated
3. **Context injection** — feedback ritorna all'agent per fix

## Pro
- Zero context switch
- Cattura problemi prima della PR
- Integra nel workflow AI coding

## Contro
- Rate limited free tier
- Dipendenza da servizio esterno

## Idee Riutilizzabili
- Pre-commit hook con AI review
- Feedback loop agent ← reviewer
- "AI slop detection" come feature
