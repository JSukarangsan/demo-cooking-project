---
name: feature-brief
description: >
  Write a feature brief or PRD grounded in project context.
  Reads project.md for problem framing, goals, and constraints.
  Produces a structured brief with problem statement, scope, requirements,
  acceptance criteria, open questions, and success metrics.
  Use when someone says "write a feature brief", "draft a PRD",
  "spec out [feature]", or "write up [feature name]".
---

# Feature Brief Skill

Writes a grounded feature brief — not a generic template, but one that traces back to the actual project context.

## What I Need
- Feature name and description
- The problem it solves (or I'll pull from project.md if it's the core problem)
- Any constraints or decisions already made

## What I'll Produce
- `{feature-name}-brief.md` written to this folder

## What Goes In It
- Problem statement (user + business)
- Scope: in scope / out of scope / explicitly deferred
- Requirements (user stories or job stories format)
- Acceptance criteria
- Open questions and dependencies
- Success metrics (tied to North Star from project.md)

## Full Workflow
See `references/workflow.md` in this skill directory for the interview guide and output format.
