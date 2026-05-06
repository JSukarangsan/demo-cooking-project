---
name: log-decision
description: >
  Log a decision to decisions.md with minimal friction.
  Works two ways: state the decision directly ("we decided to X because Y")
  or paste raw text (meeting notes, Slack thread, email) and I'll extract
  decisions automatically. Writes immediately — no long confirmation loops.
  Use when someone says "log this decision", "we just decided X",
  "add to decision log", or pastes meeting notes containing decisions.
---

# Log Decision Skill

Makes it dead easy to keep decisions.md current.

## What I Need
Either:
- A direct statement of what was decided (I'll ask at most 3 gap-fill questions)
- Pasted raw text — I'll extract decision-shaped statements and confirm before writing

## What I'll Do

**Direct statement path:**
Parse the decision, ask only for missing gaps (who decided, why, alternatives considered), write immediately. No confirmation loop.

**Raw text path:**
Extract all decisions from the text, show a quick list for confirmation, write confirmed ones. Flag uncertain items as potential open questions for todo.md.

## What Gets Written
Each entry in decisions.md includes:
- Status: `open | closed | superseded`
- Decision maker
- What was decided
- Why
- Alternatives considered
- Impact
- Tags (inferred automatically)

## Managing the log
- "Change [decision] to closed" → updates the status field
- "We reversed [decision]" → marks old one as superseded, logs the new one
- Newest entries always go at the top

## Full Workflow
See `assembly/log-decision.yaml` in the Kit Builder repo for the complete extraction and writing logic.
