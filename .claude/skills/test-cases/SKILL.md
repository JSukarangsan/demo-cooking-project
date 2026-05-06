---
name: test-cases
description: >
  Generate PM-level acceptance criteria and test cases from a feature brief or PRD.
  Reads the brief, checks decisions.md for open questions that could affect requirements,
  checks constraints.md for hard limits, and produces a structured handoff doc
  organized by P0 / P1 / P2 priority.

  Use when someone says "write test cases for [feature]", "generate acceptance criteria",
  "create a handoff spec", "what needs to pass before we ship", or references a
  feature brief with "generate test cases".
---

# Test Cases Skill

Turns a feature brief into PM-level acceptance criteria — the scenarios engineering
needs to verify before shipping, organized by priority.

## What I Need
- A feature brief or PRD (@ reference a file or paste the content)
- Optionally: a specific area to focus on ("focus on cold start handling")

## What I'll Produce
- `{feature-name}-handoff.md` — acceptance criteria and test cases by P0 / P1 / P2,
  open decisions flagged, PRD gaps called out

## What P0 / P1 / P2 Means Here
- **P0** — Must pass before launch. Core happy paths + guardrail checks.
- **P1** — Should test before launch. Edge cases, error states, degraded experiences.
- **P2** — Regression / good to have. Secondary paths, non-critical edge cases.

## Full Workflow
See `references/workflow.md` in this skill directory.
