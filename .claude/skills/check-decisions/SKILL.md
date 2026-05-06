---
name: check-decisions
description: >
  Query the decision log to find out if something has been decided.
  Ask in natural language — I'll search decisions.md, return the matching
  entry with full context and status, and tell you whether it's still live.
  Use when someone says "has X been decided?", "what did we decide about Y?",
  "is Z settled?", or any question about whether a decision exists.
---

# Check Decisions Skill

Keeps settled questions settled.

## What I Need
- A natural language question about a decision ("has the legal review been done?" / "what did we decide on cold start?")

## What I'll Do
1. Read decisions.md
2. Find entries relevant to your question (semantic match — not just keywords)
3. Return the full entry: what was decided, when, who, why, and what it means for your question
4. Flag whether the decision is `open` (not fully resolved) or `closed`

## If Nothing Is Found
I'll say so clearly and offer to:
1. Log it as an open question in todo.md
2. Log a new decision now if it's been resolved
3. Skip it — treat as undecided

## What This Doesn't Do
- Doesn't query Slack or Glean (only reads local decisions.md)
- Doesn't reopen closed decisions without you asking

## Full Workflow
See `assembly/check-decisions.yaml` in the Kit Builder repo for the matching and response logic.
